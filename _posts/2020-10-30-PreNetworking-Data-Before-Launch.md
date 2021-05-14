---
layout: post
title: PreNetworking Data Before Launch
visible: 1
---

Instead of asynchronously updating the UI while performing the networking, I tried pre-networking the data by using a dummy launch screen. 



Originally in iOS, it's possible to make an actual launch screen for your app when it boots up. 

The dummy launch screen I made is a simple View Controller that looks visually identical to my actual launch screen, and it acts as if it is the same. 
The under-the-hood purpose of it is to perform networking tasks and instantiate the real initial View Controller when networking finishes. 
<br>

It flows like this... After my real launch screen should finish, the app will initialize on my dummy launch screen, which will then initialize the actual destination and send the networked data.

<h3>Procedure</h3>

<ol>
  <li>Actual launch screen takes place.</li>
  <li>Initializes on my dummy launch screen VC.</li>
  <li>It networks data from firestore.</li>
  <li>When complete, will initialize the true destination VC, and passes on networked data.</li>
</ol> 

```swift
class DummyLaunchViewController: UIViewController {
    let firestoreManager = FirestoreManager()
    var data = [[String: [Product]]]()
    override func viewDidLoad() {
        super.viewDidLoad()
        getData()
    }
    func getData() {
        firestoreManager.downloadData() { data, err in
            if let err = err {
                // **Create error alert**
                return
            }
            self.data = data
            print("Pre Transition:", self.data)
            
            let homeTabBarVC = self.storyboard?.instantiateViewController(identifier: K.storyboardID.HomeTabBarVC) as! UITabBarController
            
            // 1st VC
            let firstDestinationVC = homeTabBarVC.viewControllers?[0] as! HomeViewController
            firstDestinationVC.data = self.data
            // MARK: TODO --> 2nd VC (Create later)
            // ...
            self.view.window?.rootViewController = homeTabBarVC
            self.view.window?.makeKeyAndVisible()
        }
    }
}
```

<div align="center">
<img src="{{ site.baseurl }}/images/10_30_2020/preloading_clip.gif" alt="clip" width="400" height="340"/>
</div>
The gif quality is bad... but see how the dummy launch screen is unnoticable.

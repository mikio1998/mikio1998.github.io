---
layout: post
title: App Rework Day One
---


On the first day, I decided to start on the collection view that will be the products navigator/manual. I will use xib to design the cells I will use in my project. I also keep my project organized using better constants.

<h3>What I’m doing differently:</h3>
Xib files for cells.
MVP structure for this project.
Constants are kept much safer and organized.

<div align="center">
<img src="{{ site.baseurl }}/images/10_5_2020/collection_view.png" alt="OldFirestore" width="300" height="208"/>
</div>

<h5>Cells</h5>
Each cell has a product name and image. 

<div align="center">
<img src="{{ site.baseurl }}/images/10_5_2020/collection_cell.png" alt="OldFirestore" width="300" height="208"/>
</div>

```swift
class ProductCell: UICollectionViewCell {

    @IBOutlet weak var stackView: UIStackView!
    
    @IBOutlet weak var image: UIImageView!
    @IBOutlet weak var label: UILabel!
    
    override func awakeFromNib() {
        super.awakeFromNib()
        // Initialization code
        
        //MARK:Center StackView X and Y
        self.addConstraint(NSLayoutConstraint(
            item: self.stackView!,
            attribute: NSLayoutConstraint.Attribute.centerX,
            relatedBy: NSLayoutConstraint.Relation.equal,
            toItem: self,
            attribute: NSLayoutConstraint.Attribute.centerX,
            multiplier: 1, constant: 0))
        
        self.addConstraint(NSLayoutConstraint(
            item: self.stackView!,
            attribute: NSLayoutConstraint.Attribute.centerY,
            relatedBy: NSLayoutConstraint.Relation.equal,
            toItem: self,
            attribute: NSLayoutConstraint.Attribute.centerY,
            multiplier: 1, constant: 0))
        

        //MARK:Set Stackview Height&Width
        self.addConstraint(NSLayoutConstraint(
            item: self.stackView!,
            attribute: NSLayoutConstraint.Attribute.width,
            relatedBy: NSLayoutConstraint.Relation.equal,
            toItem: nil,
            attribute: NSLayoutConstraint.Attribute.notAnAttribute,
            multiplier: 1, constant: K.ObjectSizes.ProductsPage.CollectionCell.cellWidth))
        
        self.addConstraint(NSLayoutConstraint(
            item: self.stackView!,
            attribute: NSLayoutConstraint.Attribute.height,
            relatedBy: NSLayoutConstraint.Relation.equal,
            toItem: nil,
            attribute: NSLayoutConstraint.Attribute.notAnAttribute,
            multiplier: 1, constant: K.ObjectSizes.ProductsPage.CollectionCell.cellHeight))
    }
}

```

<h5>Collection</h5>
The collection will have 2 cells per row, with a brand title at the top. 
```swift
// view code
```

<h5>Constants</h5>
For structure, I am keeping central information such as identifiers, keys, paths, and values in a struct.
(Picture of constants.swift)
```swift
// const code
```
In the sub struct ObjectSizes, I decided to keep object sizes and sizing logic in Constants. The reason is because I was struggling to display proportional cells in my collection view. So, I made cell size a constant and applied them both to the cell itself and the collection view layout sizeforitemat.

There must be a better method to this which I will find later.




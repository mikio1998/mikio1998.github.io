---
layout: post
title: Enum Notes  
---
<h3>Enums</h3>
Enums in Swift are used to create your own type of value. They can be incredibly useful when used with switch statements. 

I simply explain the benefits of using enums when dealing with conditions.
Here, I have a function that gives different opinions for weather.


```swift
// Example #1
// Sample code without using enum

func howsTheWeather(weather: String) -> String {
    if weather == "sun" {
        return "Great"
    } else {
        return "Gloomy"
    }
}
```

Some issues:
<ul>
  <li> It's not just sunny weather.
      Cloudy, wind, or snow are also weather conditions. 
  <li> Erroneous typos or capital letters.
      Input errors are realistic such as "sunn". Directly using Strings like this may be risky... 
</ul>

<h3>Use an enum!</h3>

```swift
// Example #2
// Now, group weathers as a new data type using enum

enum WeatherCondition {
    case sun, rain, cloud, snow, wind 
}

func howsTheWeather(weather: WeatherCondition) -> String {
    if weather == WeatherCondition.sun || WeatherCondition.cloud || WeatherCondition.snow || WeatherCondition.wind {
        return "Great"
    } else {
        return "Gloomy"
    }
}
```
Now shorten and simplify it...
```swift
//shorter:

enum WeatherCondition {
    case sun, rain, cloud, snow, wind 
}

func howsTheWeather(weather: WeatherCondition) -> String {
    if weather == .rain {
        return "Gloomy"
    } else {
        return "Great"
    }
}
```
Here enums are applied. <b>It eliminates errors caused by typos because the new WeatherCondition type is required as an input.</b>
Also, notice the .rain instead of WeatherCondition.rain. Swift's type inference allows this, it's inferred I want to compare to WeatherCondition type. 

<h3>Switch case, and enum</h3>

Switch blocks and enums work together very effectively. You can use enum to make sure a Switch block does not leave out any potential cases.
See how switch and enum make the code much more effective:

```swift
enum WeatherCondition {
    case sun
    case rain
    case cloud
    case snow
    case wind
}

func howsTheWeather(weather: WeatherCondition) -> String {

    switch weather {
    case .sun:
        return "Not at all gloomy"
    case .cloud, .wind, .snow:
        return "Chilly but not gloomy"
    case .rain
        return "Gloomy"
    }
}
```

<h4>Switch case, and enum: case values</h4>
An enum case can have a value property, that you can define.

Example:
```swift
// Gave snow a depth property.
enum WeatherCondition {
    case sun
    case rain
    case cloud
    case snow(depth: Int) 
    case wind
}

func howsTheWeather(weather: WeatherCondition) -> String {
    switch weather {
    
    case .sun:
        return "Not at all gloomy"
    case .cloud, .wind, .snow(let depth) where depth < 10:
        return "Chilly but not gloomy"
        
    // Order matters! case .snow comes after above. Swift runs switch cases top to bottom.
    case .snow:  
        return "Drive safe!"
    
    case .rain
        return "Gloomy"
    }
}
```
The snow enum was given a depth property, to specify the amount of snowfall. Because .snow now carries this property, we can now test some conditions a bit more further. We consider that our opinion changes at 10 inches of snow, where any less value will still be "Chilly but not gloomy," but any greater value will be given a new case of "Drive safe!". 

In the switch statement, .snow now appears in two cases. Which case bound to be called depends on the value.

<h4>Syntax of the example.<h4>
    
```swift
// Use "let" to get a hold of the value inside the enum.
// Then, use "where" to check condition

case .cloud, .wind, .snow(let depth) where depth < 10:
```



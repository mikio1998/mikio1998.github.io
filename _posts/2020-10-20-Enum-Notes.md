---
layout: post
title: Enum  
---

Unfinished

Code #1
```swift

// assume you don't like rain
//bad example: without enum

func gloomyWeather(weather: String) -> String {
    if weather == "sun" {
        return nil
    } else {
        return "Gloomy"
    }
}
gloomyWeather("sun")
// -> false
```


Code #1:
<ul>
  <li> It's not just sunny weather.
      Cloudy, wind, or snow are also weather conditions. 
  <li> Erroneous typos or capital letters.
      Input errors are realistic such as "sunn". Directly using Strings like this may be risky. 
<ul>



Code #2
```swift
//better example: group weathers as a type using enum
enum WeatherCondition {
    case sun, rain, cloud, snow, wind 
}

func gloomyWeather(weather: WeatherCondition) -> String {
    if weather == WeatherCondition.sun || WeatherCondition.cloud || WeatherCondition.snow || WeatherCondition.wind {
        return nil
    } else {
        return "Gloomy"
    }
}
```
```swift
//shorter:

enum WeatherCondition {
    case sun, rain, cloud, snow, wind 
}

func gloomyWeather(weather: WeatherCondition) -> String {
    if weather == .rain {
        return "Gloomy"
    } else {
        return nil
    }
}
```
Here enums are applied. It eliminates errors caused by typos because the new WeatherCondition type is required as an input.
Also, .rain instead of WeatherCondition.rain. Swift's type inference allows this, it's inferred I want to compare to WeatherCondition type. 









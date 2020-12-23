# AsayerTracker

[![Version](https://img.shields.io/cocoapods/v/AsayerTracker.svg?style=flat)](https://cocoapods.org/pods/AsayerTracker)
[![License](https://img.shields.io/cocoapods/l/AsayerTracker.svg?style=flat)](https://cocoapods.org/pods/AsayerTracker)
[![Platform](https://img.shields.io/cocoapods/p/AsayerTracker.svg?style=flat)](https://cocoapods.org/pods/AsayerTracker)

## Overview

Asayer is a Frontend Application Monitoring (FAM) tool. It helps developers reproduce bugs, catch errors and track the performance of their web applications.
You can find all the details on [asayer.io](https://asayer.io/).

## Requirements

* SDK supports iOS 11+

## Installation

#### Using Cocoapods
AsayerTracker is available through [CocoaPods](https://cocoapods.org). To install it, simply add the following line to your Podfile:

```ruby
pod 'AsayerTracker'
```

#### Manual Installation
The SDK is available in [Github Releases tab](https://github.com/asayerio/ios-tracker/releases) where you can download the compressed framework, you can find the latest release [here](https://github.com/asayerio/ios-tracker/releases/latest).

1. [Download](https://github.com/asayerio/ios-tracker/releases/latest) the zip file containing this repository.
2. Uncompress the zip file and then move the `AsayerTracker/Asayer.framework` artefact into your project.
3. Add `Asayer.framework` located within your project to the `Embedded binaries` section in the `General` tab of you iOS app target.

## Usage
Initialize the package from your codebase entry point and start the tracker. You must set the projectID option in the constructor. Its value can be found in your Asayer dashboard under [Preferences > Projects](https://app.asayer.io/client/projects).

```swift
import Asayer

func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

    Asayer.shared.start(projectID: "PROJECT_ID", config: nil)

    //...

    return true
}
```

### userID
Associates the userID to the recorded session. The method should be called with one string argument.

```swift
Asayer.shared.userID('user@asayer.io');
```

### userAnonymousID
Associates the userAnonymousID to the recorded session. The method should be called with one string argument.

```swift
Asayer.shared.userAnonymousID('Ishd43ada89');
```

### metadata
Associates metadata value to the current session recording. These variables should be manually added beforehand under Preferences > Metadata in your dashboard. The method should be called with two string arguments (key and value).

```swift
Asayer.shared.metadata(key: "metadataKey", value: selectedPlan.title)
```

### event
Sends custom event to the session recorder. These events are searchable by the first argument, which should be a string, and optionally can have a second argument with custom payload that should conform to Encodable.

```swift
Asayer.shared.metadata(name: "eventName", payload: selectedPlan)
```

## Author

[Asayer.io](https://asayer.io/)

## License

AsayerTracker is available under the MIT license. See the LICENSE file for more info.

# FBAudienceNetworkSPM

A Swift Package wrapper for the [Meta Audience Network SDK](https://developers.facebook.com/docs/audience-network/),  
allowing you to easily integrate Audience Network into your iOS projects using Swift Package Manager.

---

## 📦 Features
- Swift Package Manager (SPM) support for Meta Audience Network SDK.
- No need to manually drag `.framework` files into Xcode.
- Ready for use with both Objective-C and Swift projects.
- Compatible with iOS 11+.
- Lightweight wrapper — no modification to the original SDK.

---

## 🚀 Installation

### Add via Swift Package Manager
In Xcode:
1. Go to **File → Add Packages…**
2. Enter the repository URL:
https://github.com/doxuto/FBAudienceNetworkSPM.git

3. Select the latest version and add it to your project.

---

## 📋 Requirements
- iOS 11.0+
- Xcode 14+
- Swift 5.7+
- An active Meta for Developers account with configured Audience Network placements.

---

## 🛠 Usage

### 1. Import the SDK
```swift
import UIKit
import FBAudienceNetwork

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication,
                     didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        FBAdSettings.setLogLevel(.log)
        return true
    }
}
```

### 2. Initialize Audience Network in AppDelegate
```swift
import UIKit
import FBAudienceNetwork

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication,
                     didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        FBAdSettings.setLogLevel(.log)
        return true
    }
}
```

### 3. Load an Interstitial Ad
```swift
import UIKit
import FBAudienceNetwork

class ViewController: UIViewController, FBInterstitialAdDelegate {
    var interstitialAd: FBInterstitialAd?

    override func viewDidLoad() {
        super.viewDidLoad()
        interstitialAd = FBInterstitialAd(placementID: "YOUR_PLACEMENT_ID")
        interstitialAd?.delegate = self
        interstitialAd?.load()
    }

    func interstitialAdDidLoad(_ interstitialAd: FBInterstitialAd) {
        interstitialAd.show(fromRootViewController: self)
    }
}
```

## ⚙️ How It Works
This Swift Package bundles the **Meta Audience Network iOS SDK** as a precompiled **static framework** inside the package.  
It then exposes it through a `binaryTarget` in `Package.swift`, allowing you to import and use the SDK without manual framework integration.

**Advantages:**
- Easy updates via SPM.
- Works out of the box for both Swift and Objective-C projects.
- No manual copying of `.framework` files.

---

## ⚠️ Important Notes
- Make sure you have configured your **Audience Network** placement IDs in the [Meta for Developers dashboard](https://developers.facebook.com/apps/).
- Ensure your app complies with **Meta Audience Network** [policies](https://developers.facebook.com/docs/audience-network/policy/).
- For iOS 14+, you may need to handle **App Tracking Transparency (ATT)** prompts before showing ads.

---

## 📄 License
This package is only a wrapper. The original **Meta Audience Network SDK** is distributed under its own license from Meta.  
See [Meta Audience Network Terms](https://developers.facebook.com/terms).

---

## 🔗 Resources
- [Meta Audience Network Documentation](https://developers.facebook.com/docs/audience-network/)
- [Swift Package Manager Documentation](https://developer.apple.com/documentation/swift_packages/)
- [Meta Audience Network Policy](https://developers.facebook.com/docs/audience-network/policy/)

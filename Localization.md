# Localization in iOS using UIKit

Localization in iOS allows your app to support multiple languages. Here’s how you can localize your UIKit-based app step by step:

<details>
<summary>**1. Enable Localization in Xcode**</summary>

1. Open your project in Xcode.
2. Select your project file in the **Project Navigator**.
3. Go to the **Info** tab.
4. Under **Localizations**, click the `+` button to add the languages you want to support.

</details>

<details>
<summary>**2. Localize Your Strings**</summary>

### Create a `Localizable.strings` File:
1. Right-click on the **Supporting Files** folder (or any folder in your project) and select **New File**.
2. Choose **Strings File** and name it `Localizable.strings`.

### Add Translations:
1. Select the `Localizable.strings` file in the Project Navigator.
2. Click the **Localize...** button in the File Inspector.
3. Choose the languages you want to localize (e.g., English, Spanish). Xcode will create separate `.strings` files for each language.

Example:
- **English (Base):**
  ```swift
  "welcome_message" = "Welcome!";
  "logout_button" = "Logout";
  ```
- **Spanish:**
  ```swift
  "welcome_message" = "¡Bienvenido!";
  "logout_button" = "Cerrar sesión";
  ```

</details>

<details>
<summary>**3. Update Your UIKit Code**</summary>

Use `NSLocalizedString` to fetch localized strings in your app:
```swift
label.text = NSLocalizedString("welcome_message", comment: "Welcome message on the home screen")
button.setTitle(NSLocalizedString("logout_button", comment: "Logout button title"), for: .normal)
```

</details>

<details>
<summary>**4. Localize Storyboards and XIB Files**</summary>

1. Open your storyboard or XIB file.
2. Select the file in the **Project Navigator**.
3. In the **File Inspector**, check the **Base Internationalization** checkbox (if not already enabled).
4. Click the **Localize...** button and choose the languages to localize.
5. Xcode will generate separate `.strings` files for each storyboard/XIB file for each language. Edit these files to provide translations for UI elements.

</details>

<details>
<summary>**5. Localize Images and Assets (Optional)**</summary>

1. In the **Assets.xcassets** folder, select the image or asset.
2. Click the **Localize** button in the File Inspector.
3. Add different versions of the image for each language.

</details>

<details>
<summary>**6. Test Localization**</summary>

1. Go to **Scheme Menu > Edit Scheme > Run > Options**.
2. Under **Application Language**, select the language you want to test.
3. Run the app in the simulator or on a device to see the localized content.

</details>

<details>
<summary>**7. Change Language Programmatically (Optional)**</summary>

To allow users to change the app’s language within the app:

1. Create a mechanism to load the appropriate `.strings` file based on the selected language.
2. Use the `Bundle` class to load strings for the selected language:

```swift
extension Bundle {
    private static var onLanguageDispatchOnce: Void = {
        object_setClass(Bundle.main, CustomBundle.self)
    }()

    var localizedBundle: Bundle? {
        return objc_getAssociatedObject(self, &bundleKey) as? Bundle
    }

    public static func setLanguage(_ language: String) {
        objc_setAssociatedObject(Bundle.main, &bundleKey, Bundle(path: Bundle.main.path(forResource: language, ofType: "lproj") ?? ""), .OBJC_ASSOCIATION_RETAIN_NONATOMIC)
        onLanguageDispatchOnce
    }
}

class CustomBundle: Bundle {
    override func localizedString(forKey key: String, value: String?, table tableName: String?) -> String {
        return (self.localizedBundle ?? self).localizedString(forKey: key, value: value, table: tableName)
    }
}
```

Call `Bundle.setLanguage("es")` to switch to Spanish, for example.
https://chatgpt.com/share/678240ac-6c34-800d-a7f5-6133b9d17a38
https://medium.com/@itsuki.enjoy/localization-in-ios-swift-6b3a7735bd1a

</details>

By following these steps, you can successfully localize your iOS app using UIKit. Let me know if you need further assistance!

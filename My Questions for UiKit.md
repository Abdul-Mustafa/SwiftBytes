<details>
    <summary>
        1.what is User Defaults?
    </summary>  
   # UserDefaults in iOS

**UserDefaults** is a built-in storage mechanism in iOS that allows you to save and retrieve small pieces of data persistently. It is ideal for lightweight data storage such as user preferences, app settings, or UI state.

---

## Key Features of UserDefaults

- **Key-Value Storage:** Data is stored as key-value pairs. Example: `UserDefaults.standard.set(true, forKey: "isDarkModeEnabled")`
- **Persistent Storage:** Once saved, data remains available until explicitly removed.
- **Quick and Lightweight:** Best suited for small amounts of data like preferences or settings.
- **Thread-Safe:** Can be safely accessed from multiple threads.

---

## Data Types Supported by UserDefaults

- **Primitive Types:** `Bool`, `Int`, `Float`, `Double`
- **Collections:** `String`, `Array`, `Dictionary`
- **Dates:** `Date`
- **Custom Data:** Encodable data using `Codable`

---

## Common UserDefaults Methods

### Save Data
```swift
UserDefaults.standard.set(true, forKey: "SwitchState")
```
Saves the value `true` under the key `"SwitchState"`.

### Retrieve Data
```swift
let switchState = UserDefaults.standard.bool(forKey: "SwitchState")
```
Retrieves the value associated with the key `"SwitchState"`. Returns `false` if the key does not exist.

### Remove Data
```swift
UserDefaults.standard.removeObject(forKey: "SwitchState")
```
Deletes the value associated with the key `"SwitchState"`.

---

## When to Use UserDefaults

- Save **user preferences** (e.g., theme mode, font size).
- Store **simple app settings** (e.g., last visited screen).
- Persist **small pieces of data** across app sessions.

---

## Limitations of UserDefaults

- **Not for Large Data:** Avoid storing large datasets like images or files. Use Core Data or the file system instead.
- **Not Secure:** Data is not encrypted. Avoid storing sensitive information like passwords or tokens.
- **Performance:** Overloading UserDefaults with too much data can slow performance.

---

## Example: Using UserDefaults

```swift
// Save a user preference
UserDefaults.standard.set("Dark", forKey: "AppTheme")

// Retrieve the preference
let theme = UserDefaults.standard.string(forKey: "AppTheme") ?? "Light"

// Remove the preference
UserDefaults.standard.removeObject(forKey: "AppTheme")
```

### Explanation:
- The app theme is saved as `"Dark"`.
- Later, the theme is retrieved, defaulting to `"Light"` if no value exists.
- Finally, the preference is removed from UserDefaults.

---

By understanding and leveraging UserDefaults, you can create more personalized and persistent user experiences in your iOS applications.


</details>
<details>
<summary>Why we do not create an instance of the `UserDefaults` class in UIKit?</summary>

In iOS development, `UserDefaults` is a singleton class, which means you do not need to create an instance of it. Instead, you can directly use its shared instance via `UserDefaults.standard`. This is due to the **singleton pattern**, which ensures there is only one instance of `UserDefaults` for the entire application.

### Explanation:

- **Singleton Pattern**: The singleton pattern ensures that a class has only one instance throughout the application’s lifecycle. The shared instance of `UserDefaults` is accessed through `UserDefaults.standard`, meaning you do not need to create an object of `UserDefaults` to use it.
  
- **Why No Instance Creation?**: Since `UserDefaults` follows the singleton pattern, calling `UserDefaults.standard` gives you access to the same instance every time. This avoids the need to instantiate it repeatedly, making the code simpler and more memory-efficient.

Here’s an example of how you use it:

```swift
// Saving a value
UserDefaults.standard.set("Hello, World!", forKey: "greeting")

// Retrieving a value
let greeting = UserDefaults.standard.string(forKey: "greeting")

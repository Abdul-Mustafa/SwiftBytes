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
    <summary>2. Why do we not create a new instance for UserDefaults in UIKit?</summary> <p style="background-color: #f0f8ff; color: #333333;"> In UIKit (and iOS development in general), <code>UserDefaults</code> is a shared system that allows your app to store small amounts of data persistently. The reason we don't create a new instance of <code>UserDefaults</code> is because it is designed to be a <strong>singleton</strong>. <h3>1. Singleton Pattern</h3> <p><code>UserDefaults</code> is a <strong>singleton</strong> class, meaning there is only one instance of it throughout the entire app. The system manages the shared data storage across all parts of the app, ensuring consistency. Creating new instances would lead to separate, unshared storage, which could cause unexpected behavior and data loss or duplication.</p> <h3>2. Access to Shared Storage</h3> <p>The singleton instance of <code>UserDefaults</code> ensures that all settings and preferences are centralized and accessible from any part of the app. By using <code>UserDefaults.standard</code>, you're accessing the shared, globally available instance of the class.</p> <h3>3. Efficient Memory Management</h3> <p>Since <code>UserDefaults</code> is managed as a singleton, it’s optimized for memory and performance. Creating multiple instances would waste resources, as each instance would create its own storage reference and could lead to inefficient memory usage.</p> <h3>4. Convenience</h3> <p>Using <code>UserDefaults.standard</code> allows for a consistent, easy-to-use interface for storing and retrieving small pieces of persistent data, like user preferences, settings, or app state. Having only one instance simplifies the development process and reduces the chance for errors.</p> <h3>Example:</h3> <pre> // Correct approach: Accessing the shared instance UserDefaults.standard.set("value", forKey: "key")
// Wrong approach: Creating a new instance (unnecessary) let userDefaults = UserDefaults() userDefaults.set("value", forKey: "key") </pre>

<p>In summary, the <code>UserDefaults</code> class is designed as a singleton to provide a single, shared instance that can be accessed from anywhere in the app, ensuring data consistency and efficient resource usage. Therefore, we should always use <code>UserDefaults.standard</code>.</p> </p> </details>

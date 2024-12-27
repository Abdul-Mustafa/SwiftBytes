<details>
    <summary>
        what is User Defaults?
    </summary>  
    UserDefaults is a built-in storage mechanism in iOS that allows you to save and retrieve small pieces of data persistently. It is designed for lightweight data storage, such as user preferences, app settings, or the state of the UI.

When you store data in UserDefaults, it is automatically saved to the device’s local storage and persists even if the app is closed or the device is restarted.

Key Features of UserDefaults
Key-Value Storage:

Data is stored as key-value pairs, where each value is associated with a unique key.
Example: UserDefaults.standard.set(true, forKey: "isDarkModeEnabled")
Persistent Storage:

Once data is saved, it remains available until explicitly removed.
Quick and Lightweight:

Ideal for storing small amounts of data like user settings or app preferences.
Not suitable for large datasets like images, videos, or files.
Thread-Safe:

It can be safely accessed from multiple threads.
Data Types Supported by UserDefaults
UserDefaults can store:

Primitive Types:
Bool (true/false)
Int (e.g., 42)
Float (e.g., 3.14)
Double (e.g., 123.456)
Collections:
String (e.g., "Hello")
Array
Dictionary
Dates: Date
Custom Data: You can also store custom data by encoding it as Data using Codable.
Common UserDefaults Methods
Save Data to UserDefaults:

swift
Copy code
UserDefaults.standard.set(true, forKey: "SwitchState")
Saves the value true under the key "SwitchState".
Retrieve Data from UserDefaults:

swift
Copy code
let switchState = UserDefaults.standard.bool(forKey: "SwitchState")
Retrieves the value associated with the key "SwitchState". If the key does not exist, it returns the default value (false for Bool).
Remove Data:

swift
Copy code
UserDefaults.standard.removeObject(forKey: "SwitchState")
Deletes the value associated with the key "SwitchState".
When to Use UserDefaults
Save user preferences (e.g., theme mode, font size).
Store simple app settings (e.g., last visited screen).
Persist small pieces of data that need to be available across app sessions.
Limitations of UserDefaults
Not for Large Data:

Do not use it to store files, images, or large datasets. Use a database (e.g., Core Data) or file system instead.
Not Secure:

Data in UserDefaults is not encrypted. Avoid storing sensitive information like passwords or tokens directly.
Performance:

It is designed for quick and lightweight access but can become slow if overloaded with too much data.
Example: Using UserDefaults
swift
Copy code
// Save a user preference
UserDefaults.standard.set("Dark", forKey: "AppTheme")

// Retrieve the preference
let theme = UserDefaults.standard.string(forKey: "AppTheme") ?? "Light"

// Remove the preference
UserDefaults.standard.removeObject(forKey: "AppTheme")
In this example:

The app theme is saved as "Dark".
Later, the theme is retrieved, defaulting to "Light" if no value exists.
Finally, the preference is removed from UserDefaults.

</details>

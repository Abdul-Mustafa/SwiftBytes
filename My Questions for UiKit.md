<details>
    <summary>
        what is User Defaults?
    </summary>  
    <body style="font-family: Arial, sans-serif; line-height: 1.6; margin: 0; padding: 0; background-color: #f4f4f9; color: #333;">
    <div style="max-width: 800px; margin: 20px auto; background: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);">
        <h1 style="color: #0056b3;">UserDefaults in iOS</h1>
        <p><strong>UserDefaults</strong> is a built-in storage mechanism in iOS that allows you to save and retrieve small pieces of data persistently. It is ideal for lightweight data storage such as user preferences, app settings, or UI state.</p>

        <h2 style="color: #0056b3;">Key Features of UserDefaults</h2>
        <ul style="list-style: disc inside; margin: 10px 0; padding: 0 20px;">
            <li><strong>Key-Value Storage:</strong> Data is stored as key-value pairs. Example: <code>UserDefaults.standard.set(true, forKey: \"isDarkModeEnabled\")</code></li>
            <li><strong>Persistent Storage:</strong> Once saved, data remains available until explicitly removed.</li>
            <li><strong>Quick and Lightweight:</strong> Best suited for small amounts of data like preferences or settings.</li>
            <li><strong>Thread-Safe:</strong> Can be safely accessed from multiple threads.</li>
        </ul>

        <h2 style="color: #0056b3;">Data Types Supported by UserDefaults</h2>
        <ul style="list-style: disc inside; margin: 10px 0; padding: 0 20px;">
            <li><strong>Primitive Types:</strong> <code>Bool</code>, <code>Int</code>, <code>Float</code>, <code>Double</code></li>
            <li><strong>Collections:</strong> <code>String</code>, <code>Array</code>, <code>Dictionary</code></li>
            <li><strong>Dates:</strong> <code>Date</code></li>
            <li><strong>Custom Data:</strong> Encodable data using <code>Codable</code></li>
        </ul>

        <h2 style="color: #0056b3;">Common UserDefaults Methods</h2>
        <h3 style="color: #0056b3;">Save Data</h3>
        <pre style="background: #f1f1f1; padding: 10px; border-radius: 4px; overflow-x: auto;"><code>UserDefaults.standard.set(true, forKey: "SwitchState")</code></pre>
        <p>Saves the value <code>true</code> under the key <code>"SwitchState"</code>.</p>

        <h3 style="color: #0056b3;">Retrieve Data</h3>
        <pre style="background: #f1f1f1; padding: 10px; border-radius: 4px; overflow-x: auto;"><code>let switchState = UserDefaults.standard.bool(forKey: "SwitchState")</code></pre>
        <p>Retrieves the value associated with the key <code>"SwitchState"</code>. Returns <code>false</code> if the key does not exist.</p>

        <h3 style="color: #0056b3;">Remove Data</h3>
        <pre style="background: #f1f1f1; padding: 10px; border-radius: 4px; overflow-x: auto;"><code>UserDefaults.standard.removeObject(forKey: "SwitchState")</code></pre>
        <p>Deletes the value associated with the key <code>"SwitchState"</code>.</p>

        <h2 style="color: #0056b3;">When to Use UserDefaults</h2>
        <ul style="list-style: disc inside; margin: 10px 0; padding: 0 20px;">
            <li>Save <strong>user preferences</strong> (e.g., theme mode, font size).</li>
            <li>Store <strong>simple app settings</strong> (e.g., last visited screen).</li>
            <li>Persist <strong>small pieces of data</strong> across app sessions.</li>
        </ul>

        <h2 style="color: #0056b3;">Limitations of UserDefaults</h2>
        <ul style="list-style: disc inside; margin: 10px 0; padding: 0 20px;">
            <li><strong>Not for Large Data:</strong> Avoid storing large datasets like images or files. Use Core Data or the file system instead.</li>
            <li><strong>Not Secure:</strong> Data is not encrypted. Avoid storing sensitive information like passwords or tokens.</li>
            <li><strong>Performance:</strong> Overloading UserDefaults with too much data can slow performance.</li>
        </ul>

        <h2 style="color: #0056b3;">Example: Using UserDefaults</h2>
        <pre style="background: #f1f1f1; padding: 10px; border-radius: 4px; overflow-x: auto;"><code>// Save a user preference
UserDefaults.standard.set("Dark", forKey: "AppTheme")

// Retrieve the preference
let theme = UserDefaults.standard.string(forKey: "AppTheme") ?? "Light"

// Remove the preference
UserDefaults.standard.removeObject(forKey: "AppTheme")</code></pre>
        <p>In this example:</p>
        <ul style="list-style: disc inside; margin: 10px 0; padding: 0 20px;">
            <li>The app theme is saved as <code>"Dark"</code>.</li>
            <li>Later, the theme is retrieved, defaulting to <code>"Light"</code> if no value exists.</li>
            <li>Finally, the preference is removed from UserDefaults.</li>
        </ul>
    </div>

</details>

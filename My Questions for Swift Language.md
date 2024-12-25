<details>
    <summary>1.Generic Classes in Swift?</summary>
Answer:A generic class is a class that can operate on types that are specified when the class is instantiated. The generic type is represented using type parameters, enclosed in angle brackets (<T>), where T is a placeholder name for the type.

Syntax for Generic Classes
Here’s the basic syntax for defining a generic class:

swift
Copy code
class GenericClass<T> {
    var value: T
    
    init(value: T) {
        self.value = value
    }
    
    func display() {
        print("The value is \(value)")
    }
}
Example Usage
You can create instances of this class with different types:

swift
Copy code
let intInstance = GenericClass<Int>(value: 10)
intInstance.display() // Output: The value is 10

let stringInstance = GenericClass<String>(value: "Hello")
stringInstance.display() // Output: The value is Hello
Multiple Type Parameters
You can define a class with multiple generic type parameters:

swift
Copy code
class Pair<K, V> {
    var key: K
    var value: V
    
    init(key: K, value: V) {
        self.key = key
        self.value = value
    }
    
    func display() {
        print("Key: \(key), Value: \(value)")
    }
}
Example Usage
swift
Copy code
let pair = Pair<String, Int>(key: "Age", value: 25)
pair.display() // Output: Key: Age, Value: 25
Constraints in Generic Classes
You can restrict the types that can be used with a generic class using constraints. For example, you might require that a type conforms to a certain protocol or inherits from a specific class:

swift
Copy code
class ConstrainedGenericClass<T: Numeric> {
    var value: T
    
    init(value: T) {
        self.value = value
    }
    
    func square() -> T {
        return value * value
    }
}
Example Usage
swift
Copy code
let number = ConstrainedGenericClass<Double>(value: 5.5)
print(number.square()) // Output: 30.25
Key Points
T is just a placeholder: You can use any name instead of T, like Element, Key, Value, etc.
Type safety: Swift ensures that the type you use matches the expected type when you instantiate the class.
Constraints: Use where or : to restrict the generic type.
Generics provide powerful abstraction and flexibility while maintaining the safety of Swift's strong type system.
</details>
<details>
<summary>
How to use ?? and ? in swift?
</summary>
https://chatgpt.com/share/676bd04b-e570-800d-aa10-04c9e1956495
</details>

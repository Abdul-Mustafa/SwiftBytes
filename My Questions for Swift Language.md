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
<details>
    <summary>
        How to define function in Swift?
    </summary>
</details>

<details><summary>
    What are Closures, how they are different from arrow function?
</summary>
# Closures in Swift

Closures are self-contained blocks of functionality that can be passed around and used in your code. They can capture and store references to variables and constants from the surrounding context. Swift's closures are similar to lambdas in other programming languages.

---

## Syntax

The basic syntax of a closure looks like this:

```swift
{ (parameters) -> returnType in
    // Code
}
```

### Example:

```swift
let greetClosure = { (name: String) -> String in
    return "Hello, \(name)!"
}

print(greetClosure("Hamid"))  // Output: Hello, Hamid!
```

---

## Features of Closures

1. **Inline Functionality**: Closures can be used inline in your code.
2. **Capture Values**: Closures can capture and modify values from their surrounding scope.
3. **Type Inference**: Swift can infer the parameter and return types of a closure.
4. **Shorthand Argument Names**: Closures can use shorthand argument names like `$0`, `$1`, etc.
5. **Trailing Closure Syntax**: Closures can be written outside the parentheses of a function.

---

## Closures as Variables

Closures can be assigned to variables and constants.

```swift
let addition = { (a: Int, b: Int) -> Int in
    return a + b
}

let result = addition(4, 5)
print(result)  // Output: 9
```

---

## Closures as Function Parameters

Closures are often used as parameters to functions.

### Example:

```swift
func performOperation(_ operation: (Int, Int) -> Int, _ a: Int, _ b: Int) {
    print("Result: \(operation(a, b))")
}

performOperation({ (a, b) -> Int in
    return a * b
}, 3, 4)  // Output: Result: 12
```

### Using Trailing Closure Syntax:

```swift
performOperation(3, 4) { (a, b) -> Int in
    return a - b
}  // Output: Result: -1
```

---

## Capturing Values

Closures capture constants and variables from the surrounding context. Capturing happens by reference, not by value.

### Example:

```swift
func makeIncrementer(increment: Int) -> () -> Int {
    var total = 0
    let incrementer = {
        total += increment
        return total
    }
    return incrementer
}

let incrementByTwo = makeIncrementer(increment: 2)
print(incrementByTwo())  // Output: 2
print(incrementByTwo())  // Output: 4
```

---

## Shorthand Argument Names

Swift provides shorthand argument names like `$0`, `$1`, `$2`, etc.

### Example:

```swift
let numbers = [1, 2, 3, 4, 5]
let squaredNumbers = numbers.map { $0 * $0 }
print(squaredNumbers)  // Output: [1, 4, 9, 16, 25]
```

---

## Escaping Closures

A closure is said to "escape" when it is passed as an argument to a function but is called after the function returns. You use the `@escaping` keyword to indicate that a closure can escape.

### Example:

```swift
var completionHandlers: [() -> Void] = []

func addCompletionHandler(handler: @escaping () -> Void) {
    completionHandlers.append(handler)
}

addCompletionHandler {
    print("Closure executed!")
}

completionHandlers.first?()  // Output: Closure executed!
```

---

## Autoclosures

An autoclosure is a closure that is automatically created to wrap an expression. It takes no arguments and is used for delayed evaluation.

### Example:

```swift
func serveCustomer(_ customerProvider: @autoclosure () -> String) {
    print("Now serving \(customerProvider())")
}

serveCustomer("Hamid")  // Output: Now serving Hamid
```

---

## Common Functions Using Closures

### 1. `map(_:)`
Applies a closure to each element in a collection and returns a new collection.

```swift
let numbers = [1, 2, 3]
let doubled = numbers.map { $0 * 2 }
print(doubled)  // Output: [2, 4, 6]
```

### 2. `filter(_:)`
Returns a new collection with elements that satisfy the closure condition.

```swift
let numbers = [1, 2, 3, 4]
let evenNumbers = numbers.filter { $0 % 2 == 0 }
print(evenNumbers)  // Output: [2, 4]
```

### 3. `reduce(_:_:)`
Combines all elements of a collection into a single value.

```swift
let numbers = [1, 2, 3, 4]
let sum = numbers.reduce(0) { $0 + $1 }
print(sum)  // Output: 10
```

---

## Conclusion

Closures are a powerful feature of Swift that enable functional programming paradigms, callbacks, and encapsulating functionality. They are widely used in Swift's standard library and custom code to provide concise, expressive, and reusable functionality.


</details>

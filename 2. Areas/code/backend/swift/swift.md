# Types

#### Strings
- Array of String - `private var selectedDays:Set<String> = ["Fri"]`
- Join array to singular string - `selectedDays.joined(separator: ",")`

### Constructors
```swift
init(cosmic: CosmicSDKSwift = getCosmicClient(),
        type: String) {
        self.cosmic = cosmic
        self.logger = Log.shared
        self.type = type
    }
}
```

# **Understanding Views**

- **Preview and Live Editing**: Use **`Command + Option + Enter`** to open the preview pane.
- **Changing Devices in Preview**: Adjust the target device at the top of the Xcode interface to see how your app looks on different devices.

### **Basic SwiftUI Components**

- **Creating a View**: SwiftUI views are declared as structs that conform to the **`View`** protocol.
    
    ```swift
    struct ContentView: View {
        var body: some View {
            Text("Hello, SwiftUI!")
        }
    }
    
    ```

#### Tips
##### Adding icons/emojis
Can find a full list of available emojis/icons at SF Symbols (app installed)
```swift
Label("", systemImage: "clock.badge.checkmark.fill")
```


# Testing
## UI Testing
To create a UI test, you need to add a new target with the `UI Testing Bundle`. Once created, create a new scheme to run the tests then run the commands `popod deintegrate` and `pod update` to ensure the new target is linked with the pods.

Output - generates two files, `[TARGET]Tests` and `[TARGET]LaunchTests`, make sure they both compile and run before writing any code.

Accessibility identifiers are key. Add them to the elements you intend to test to be able to search for them via tests - `.accessibilityIdentifier("RoutinesTitle")`
Example - `app.staticTexts["RoutinesTitle"] || app.buttons["RoutinesTab"]`

//TODO - how to write a good test

# **Advanced Swift Concepts**

### **ObservableObject and State Management**

- **ObservableObject**: Use for models in your app where changes should update the view.
    
    ```swift
    
    class MyViewModel: ObservableObject {
        @Published var dataProperty: String = "Initial Data"
    }
    
    ```
    
- **State**: Manage local view state with the **`@State`** property wrapper, triggering view updates on changes.
    
    ```swift
    
    struct ContentView: View {
        @State private var name = "User"
    
        var body: some View {
            Text("Hello, \(name)!")
        }
    }
    
    ```
    

### **Data Flow and Lifecycle**

- **Using Environment Variables**: Access environment variables using **`ProcessInfo`**.
    
    ```swift
    
    let configBucket = ProcessInfo.processInfo.environment["CONFIG_BUCKET"] ?? "default_value"
    
    ```
    

### **Navigation and Actions**

- Implement navigation and actions using **`NavigationView`** and **`.swipeActions`**.
    
    ```swift
    
    NavigationView {
        List {
            Text("Item 1")
            NavigationLink("Go to Details", destination: DetailView())
        }
    }
    
    ```


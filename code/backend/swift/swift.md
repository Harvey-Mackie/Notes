### Types

#### Strings
- Array of String - `private var selectedDays:Set<String> = ["Fri"]`
- Join array to singular string - `selectedDays.joined(separator: ",")`

### **Understanding Views**

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


## **Advanced Swift Concepts**

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


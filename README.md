[Exploring visionOS: Creating Side Window for Main Window with Animation](https://www.rudrank.com/exploring-visionos-creating-side-window-for-main-window-with-animation/)

![image](https://github.com/YamamotoDesu/Creating-Side-Window-for-Main-Window-with-Animation/assets/47273077/3a3247a3-8130-45b2-bb55-cf69c54ffa24)


```swift
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        .windowStyle(.plain)
    }
}

struct ContentView: View {

    @State private var showSideWindow = false

    var body: some View {
        HStack {
          VStack {
            Text("Hello, world!")
              .frame(maxWidth: .infinity, maxHeight: .infinity)
            Button(action: {
              showSideWindow.toggle()
            }, label: {
              Text("Show Side Window")
            })
            .padding()
          }
          .glassBackgroundEffect()

          if showSideWindow {
            VStack {
              Model3D(named: "Scene", bundle: realityKitContentBundle)
                .frame(maxWidth: .infinity, maxHeight: .infinity)
            }
            .frame(width: 400)
            .glassBackgroundEffect()
            .transition(.opacity)
          }
        }
        .animation(.default, value: showSideWindow)
    }
}
```

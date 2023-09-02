# USDZScanner

A SwiftUI USDZ Object Scanner for Capturing Real Life Objects and transforming to USDZ file using Photogrametry.

This is based on [Apple Object Capture Sample Code](https://developer.apple.com/documentation/realitykit/guided-capture-sample)

## Requirements

- iPhone or iPad with a LiDAR Scanner and an A14 Bionic chip or later
- iOS or iPadOS 17 or later

## Usage

Initialize USDZScanner passing the completion callback. The completion contains a parameter for the URL where it stored the USDZ file.

```swift
@main
struct SampleApp: App {

    @State var isScanObjectPresenting = false
    @State var url: URL?
    
    var body: some Scene {
        WindowGroup {
            VStack {
                
                Button("Scan Object") {
                    isScanObjectPresenting = true
                }
                
                if let url {
                    Text(url.absoluteString)
                }
                
            }
            .sheet(isPresented: $isScanObjectPresenting, content: {
                USDZScanner { url in
                    self.url = url
                    isScanObjectPresenting = false
                }
            })
        }
    }
}
```
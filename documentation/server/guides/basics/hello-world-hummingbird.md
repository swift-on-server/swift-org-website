---
layout: page
title: Hello, World! - Hummingbird
---


asdf

```swift
// swift-tools-version:5.10
import PackageDescription

let package = Package(
    name: "hello",
    platforms: [
        .macOS(.v14),
    ],
    dependencies: [
        .package(
          url: "https://github.com/hummingbird-project/hummingbird", 
          from: "2.0.0-beta.4"
        ),
        .package(
          url: "https://github.com/apple/swift-argument-parser", 
          from: "1.0.0"
        ),
    ],
    targets: [
        .executableTarget(
            name: "App",
            dependencies: [
                .product(name: "ArgumentParser", package: "swift-argument-parser"),
                .product(name: "Hummingbird", package: "hummingbird"),
            ]
        ),
    ]
)
```

asdf

```swift
// Sources/App/entrypoint.swift
import Hummingbird
import ArgumentParser

func buildApplication(
    configuration: ApplicationConfiguration
) -> some ApplicationProtocol {
    let router = Router()
    router.get("/") { _, _ in
        return "Hello"
    }

    let app = Application(
        router: router,
        configuration: configuration
    )
    return app
}

@main
struct HummingbirdArguments: AsyncParsableCommand {

    @Option(name: .shortAndLong)
    var hostname: String = "127.0.0.1"

    @Option(name: .shortAndLong)
    var port: Int = 8080

    func run() async throws {
        let app = buildApplication(
            configuration: .init(
                address: .hostname(self.hostname, port: self.port),
                serverName: "Hummingbird"
            )
        )
        try await app.runService()
    }
}
```

asdf
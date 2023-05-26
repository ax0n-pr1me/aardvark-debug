# ReadMe

## Debug rnmapbox/maps on M1

a template project to debug the integration of rnmapbox/maps with react native on M1

`npx react-native@latest init rnmapbox_m1`

```sh
❯ node --version
v18.12.1

❯ watchman --version
2023.05.15.00

echo 2.7.6 > .ruby-version

❯ ruby --version
ruby 2.7.6p219 (2022-04-12 revision c9c2245c0a) [arm64-darwin22]

```

### Verify Xcode

Xcode -> Settings -> Locations

`Xcode 14.3 (14E222b)`

```sh
❯ swift --version
swift-driver version: 1.75.2 Apple Swift version 5.8 (swiftlang-5.8.0.124.2 clang-1403.0.22.11.100)
Target: arm64-apple-macosx13.0
```

### Cocoapods

`brew install cocoapods` (note - tried other install methods, same issue)

### start project

```sh
npm run pod:install
npm run ios
```

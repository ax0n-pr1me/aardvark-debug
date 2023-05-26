# ReadMe

a template project to debug the integration of rnmapbox/maps with react native on M1

## Setup

### Environment Setup

`npx react-native@latest init aardvark_debug`

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

## start project

```sh
npm run pod:install
npm run ios
```

## Add Maps

### Install

```sh
npm install --save @rnmapbox/maps
```

### Setup Instructions

```ruby
  $RNMapboxMapsImpl = 'mapbox'
```

error below, try adding in pre and post install methods in `Podfile`

```ruby
  pre_install do |installer|
    $RNMapboxMaps.pre_install(installer)
    ... other pre install hooks
  end

    post_install do |installer|
    $RNMapboxMaps.post_install(installer)
    ... other post install hooks
  end
```

```sh
npm run pod:install

# ...
# * [RNMapbox] Changed MapboxCommon to dynamic framework
# * [RNMapbox] Changed MapboxCoreMaps to dynamic framework
# * [RNMapbox] Changed MapboxMaps to dynamic framework
# * [RNMapbox] Changed MapboxMobileEvents to dynamic framework
# * [RNMapbox] Changed Turf to dynamic framework
# * [RNMapbox] Changed MapboxCommon to dynamic framework
# * [RNMapbox] Changed MapboxCoreMaps to dynamic framework
# * [RNMapbox] Changed MapboxMaps to dynamic framework
# * [RNMapbox] Changed MapboxMobileEvents to dynamic framework
# * [RNMapbox] Changed Turf to dynamic framework
# ...
```

```sh
npm run ios
```

Same errors

```sh
Invalid react tag, could not find RCTMGLMapView

+[RCTMGLSwiftLog error:file:line:]
    RCTMGLMapViewManager.swift:33
$s13rnmapbox_maps14RCTMGLLogErroryySS_SSSutF
$s13rnmapbox_maps20RCTMGLMapViewManagerC07withMapD0_4name8rejecter2fnySo8NSNumberC_SSySSSg_AJs5Error_pSgtcyAA0cD0CctFySo12RCTUIManagerCSg_SDyAISo6UIViewCGSgtcfU_
$s13rnmapbox_maps20RCTMGLMapViewManagerC07withMapD0_4name8rejecter2fnySo8NSNumberC_SSySSSg_AJs5Error_pSgtcyAA0cD0CctFySo12RCTUIManagerCSg_SDyAISo6UIViewCGSgtcfU_TA
$sSo12RCTUIManagerCSgSDySo8NSNumberCSo6UIViewCGSgIeggg_ACSo12NSDictionaryCSgIeyByy_TR
__44-[RCTUIManager flushUIBlocksWithCompletion:]_block_invoke
__44-[RCTUIManager flushUIBlocksWithCompletion:]_block_invoke.206
__RCTExecuteOnMainQueue_block_invoke
_dispatch_call_block_and_release
_dispatch_client_callout
_dispatch_main_queue_drain
_dispatch_main_queue_callback_4CF
__CFRUNLOOP_IS_SERVICING_THE_MAIN_DISPATCH_QUEUE__
__CFRunLoopRun
CFRunLoopRunSpecific
GSEventRunModal
-[UIApplication _run]
UIApplicationMain
main
start_sim
0x0
0x0

```

```sh
 BUNDLE  ./index.js 

 LOG  Running "aardvark_debug" with {"fabric":true,"initialProps":{"concurrentRoot":true},"rootTag":1}
 WARN  Possible Unhandled Promise Rejection (id: 0):
Error: Unknown find reactTag: 12
Error: Unknown find reactTag: 12
    at promiseMethodWrapper (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:2046:45)
    at apply (native)
    at runNativeCommand (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:98117:39)
    at _runNativeCommand (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:99101:82)
    at ?anon_0_ (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:99065:57)
    at next (native)
    at asyncGeneratorStep (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:20416:26)
    at _next (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:20435:29)
    at anonymous (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:20440:14)
    at tryCallTwo (/Users/distiller/react-native/sdks/hermes/build_iphonesimulator/lib/InternalBytecode/InternalBytecode.js:61:9)
    at doResolve (/Users/distiller/react-native/sdks/hermes/build_iphonesimulator/lib/InternalBytecode/InternalBytecode.js:216:25)
    at Promise (/Users/distiller/react-native/sdks/hermes/build_iphonesimulator/lib/InternalBytecode/InternalBytecode.js:82:14)
    at anonymous (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:20432:25)
    at apply (native)
    at _runPendingNativeCommands (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:99072:52)
    at call (native)
    at _setNativeRef (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:99903:117)
    at ref (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:99949:40)
    at commitAttachRef (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:13509:29)
    at commitLayoutEffectOnFiber (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:13487:30)
    at commitLayoutMountEffects_complete (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:13950:40)
    at commitLayoutEffects_begin (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:13939:46)
    at commitLayoutEffects (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:13926:34)
    at commitRootImpl (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:15045:30)
    at commitRoot (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:14978:25)
    at performSyncWorkOnRoot (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:14640:19)
    at flushSyncCallbacks (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:6133:36)
    at workLoop (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:76246:48)
    at flushWork (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:76225:28)
    at performWorkUntilDeadline (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:76431:48)
    at apply (native)
    at anonymous (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:25946:26)
    at _callTimer (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:25865:17)
    at _callReactNativeMicrotasksPass (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:25895:17)
    at callReactNativeMicrotasks (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:26058:44)
    at __callReactNativeMicrotasks (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:2410:46)
    at anonymous (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:2222:45)
    at __guard (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:2394:15)
    at flushedQueue (http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false&modulesOnly=false&runModule=true&app=org.reactjs.native.example.aardvark-debug:2221:21)
```

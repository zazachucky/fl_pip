# fl_pip

## The picture-in-picture mode is implemented in native ios and android to display flutter's view

## Use configuration

- ios configuration : `Signing & Capabilities` -> `Capability` Add `BackgroundModes` check `Audio,AirPlay,And Picture in Picture`

- android configuration : `android/app/src/main/${your package name}/MainActivity`,

### kotlin

```kotlin

class MainActivity : FlPiPActivity()

```

### java

```java

class MainActivity extends FlPiPActivity {

}

```

android AndroidManifest file `android/app/src/main/AndroidManifest.xml`, add ` android:supportsPictureInPicture="true"`

```xml

<application android:label="FlPiP">
    <activity android:name=".MainActivity" android:launchMode="singleTop" android:supportsPictureInPicture="true" />
</application>
```

## Methods available

```dart
/// Open picture-in-picture
void enable() {
  FlPiP().enable(
      iosConfig: FlPiPiOSConfig(),
      androidConfig: FlPiPAndroidConfig(
          aspectRatio: const Rational.maxLandscape()));
}

/// Open picture-in-picture and create a new Engine
void enableWithEngine() {
  FlPiP().enableWithEngine(
      ios: const FlPiPiOSConfig(
          path: 'assets/landscape.mp4', packageName: null));
}

/// Whether to support picture in picture
void isAvailable() {
  FlPiP().isAvailable;
}

/// Picture-in-picture window state
void isActive() {
  FlPiP().isActive;
}

/// Toggle front and back
/// ios supports background switching only
void toggle() {
  FlPiP().toggle();
}

/// Quit painting in picture
void disable() {
  FlPiP().disable();
}
```

- The main method must be added to the main file if the enableWithEngine method is used

```dart
/// mainName must be the same as the method name
@pragma('vm:entry-point')
void pipMain() {
  runApp(YourApp());
}

```

## Display effect

| android                                                                                        | ios                                                                                       |
|------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| <img src="https://github.com/Wayaer/fl_pip/raw/main/example/assets/android.gif" width="100%"/> | <img src="https://github.com/Wayaer/fl_pip/raw/main/example/assets/ios.gif" width="75%"/> |

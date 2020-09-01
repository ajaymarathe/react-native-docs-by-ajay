# React Native Docs By Ajay
Simple React-Native-doc snippets.

### Use Vector Icons 

```
// Installation 
npm install --save react-native-vector-icons
```
Edit `android/app/build.gradle` ( NOT `android/build.gradle` ) and add the following:
`apply from: "../../node_modules/react-native-vector-icons/fonts.gradle"`

Edit `android/settings.gradle` to look like this (without the +):
```
rootProject.name = 'MyApp'

include ':app'

+ include ':react-native-vector-icons'
+ project(':react-native-vector-icons').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-vector-icons/android')
```
Edit `android/app/build.gradle` (note: app folder) to look like this:
```
apply plugin: 'com.android.application'

android {
  ...
}

dependencies {
  compile fileTree(dir: 'libs', include: ['*.jar'])
  compile "com.android.support:appcompat-v7:23.0.1"
  compile "com.facebook.react:react-native:+"  // From node_modules
+ compile project(':react-native-vector-icons')
}
```
Edit your `MainApplication.java` (deep in `android/app/src/main/java/...`) to look like this (note two places to edit):
```
package com.myapp;

+ import com.oblador.vectoricons.VectorIconsPackage;

....

  @Override
  protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
      new MainReactPackage()
+   , new VectorIconsPackage()
    );
  }

}
```
 
```
//Basic Exampels
import Icon from 'react-native-vector-icons/Ionicons';

function ExampleView(props) {
  return <Icon name="ios-person" size={30} color="#4F8EF7" />;
}
```

## Important Links
* [React Native Community Hooks](https://github.com/react-native-community/hooks)

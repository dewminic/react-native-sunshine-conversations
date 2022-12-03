# react-native-smooch
React Native wrapper for Smooch.io. 
This repo is forked from https://github.com/zendesk/react-native-sunshine-conversations

Modification done to mtach with the latest Android versions.


Installing Smooch on React Native
=================================

First, make sure you've [signed up for Smooch](https://app.smooch.io/signup)

If you don't already have a React Native application setup, follow the instructions [here](https://facebook.github.io/react-native/docs/getting-started.html) to create one.

Next, grab this React Native module with `yarn add @dewminic/react-native-smooch@https://github.com/dewminic/react-native-sunshine-conversations`

Link it! `npx react-native-asset react-native-smooch`

## iOS
No modification done for IOS.
Follow the same instruction to integrate with IOS as in https://github.com/zendesk/react-native-sunshine-conversations

## Android
Modification added to work with Android 13 (API level 33).

You can easily add a binding to the [Smooch Android SDK](https://github.com/smooch/smooch-android) in your React Native application by following the instructions below.

* If the Package cannot be autolinked, it can be added manually add in your `Application` class.
Add the `ReactNativeSmoochPackage` to the list of packages 

@Override
@Override
    protected List<ReactPackage> getPackages() {
      @SuppressWarnings("UnnecessaryLocalVariable")
      List<ReactPackage> packages = new PackageList(this).getPackages();
      packages.add(new ReactNativeSmoochPackage());
      return packages;
    }
```

* Add `Smooch.init` to the `onCreate` method of your `Application` class.

```java
import io.smooch.core.Settings;
import io.smooch.core.Smooch;
import io.smooch.core.SmoochCallback;
import com.facebook.soloader.SoLoader;

public class MainApplication extends Application implements ReactApplication {
    ...
    @Override
    public void onCreate() {
        super.onCreate();
        SoLoader.init(this, /* native exopackage */ false);
        Smooch.init(this, new Settings("YOUR_INTEGRATION_ID"), new SmoochCallback() {
            @Override
            public void run(Response response) {
                // Your code after init is complete
            }
        });
    }
    ...
}
```

You're now ready to start interacting with Smooch in your React Native app.

Using Smooch in your React Native App
=====================================

### Require the module
```javascript
const Smooch = require('react-native-smooch');
```

### Show the conversation screen
```javascript
Smooch.show();
```

### Set the user's first name
```javascript
Smooch.setFirstName("Kurt");
```

### Set the user's last name
```javascript
Smooch.setLastName("Osiander");
```

### Set the user's email address
```javascript
Smooch.setEmail("kurt@ralphgraciesf.com");
```

### Set the user's sign up date
```javascript
Smooch.setSignedUpAt((new Date).getTime());
```

### Associate key/value pairs with the user
```javascript
Smooch.setUserProperties({"whenDidYouFsckUp": "aLongTimeAgo"});
```

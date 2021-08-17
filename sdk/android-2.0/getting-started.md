---
title: Getting started
description: Getting started
keywords: Getting started
sort: 0
---

# Getting started

## Getting access

In order to get access to the SDK, you need to make an inquiry to sdk@movika.com or support@movika.com. After approval, you will be given a pair of **username** **password** to get
access to the library, **apiKey** and **appName** for the SDK to function.

## Add dependencies to Gradle

After gaining access, in the module level build.gradle file you need to add the repository by replacing the values of the username and password fields
with yours.

```
allprojects {
    repositories {
        maven {
            credentials {
                username "your_username"
                password "your_password"
            }
            url "https://nexus.movika.com/repository/android/"
        }
    }
}
```

Then add the dependency

```
implementation("com.movika:interactive-sdk:2.0.0")
```

## Add your ApiKey, AppName, AppVersion in Application() class

```
class App : Application() {
    override fun onCreate() {
        super.onCreate()
        MovikaSdk.setup(InitConfig(apiKey, appName, appVersion))
    }
}
```

## Create player

You can create instance of the player or get from xml

#### Creating instance

```
val interactivePlayerView = InteractivePlayerView(context)
// Add player view
yourViewGroup.addView(interactivePlayerView)
```

#### Getting from xml

```
val interactivePlayerView = findViewById<InteractivePlayerView>(R.id.your_id)
```

### Add player to Activity/Fragment lifecycle

```
lifecycle.addObserver(interactivePlayerView)
```

### Then add following in onSaveInstanceState Activity or Fragment for state saving

```
override fun onSaveInstanceState(outState: Bundle) {
    super.onSaveInstanceState(outState)
    interactivePlayerView.onSaveInstanceState(outState)
}
```

## Loading and playing

Load manifest. This example features **AsyncMovieBundleLoader**, which is implementation of **MovieBundleLoader**. Note: you can use
**DefaultStringToGameManifestConverter** if you have local manifest of String format, which is implementation of **StringToGameManifestConverter**

```
val url = "TODO URL"
AsyncMovieBundleLoader().load(url) { status ->
    if (status.isComplete && status.error != null) {
        val movieBundle = status.data!!
        interactivePlayerView.run(
            movieBundle,
            Config(),
            // Optional. Used for restoring instance state after Activity/Fragment re-creation
            savedInstanceState
        )
    }
}

```

You can check out sample app here: [link](https://github.com/movika/android.sdk.sample.movika.com)

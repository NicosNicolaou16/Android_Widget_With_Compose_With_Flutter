# Android_widget_with_compose_with_flutter

[![Linktree](https://img.shields.io/badge/linktree-1de9b6?style=for-the-badge&logo=linktree&logoColor=white)](https://linktr.ee/nicos_nicolaou)
[![Site](https://img.shields.io/badge/Site-blue?style=for-the-badge&label=Web)](https://nicosnicolaou16.github.io/)
[![X](https://img.shields.io/badge/X-%23000000.svg?style=for-the-badge&logo=X&logoColor=white)](https://twitter.com/nicolaou_nicos)
[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/nicos-nicolaou-a16720aa)
[![Medium](https://img.shields.io/badge/Medium-12100E?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@nicosnicolaou)
[![Mastodon](https://img.shields.io/badge/-MASTODON-%232B90D9?style=for-the-badge&logo=mastodon&logoColor=white)](https://androiddev.social/@nicolaou_nicos)
[![Bluesky](https://img.shields.io/badge/Bluesky-0285FF?style=for-the-badge&logo=Bluesky&logoColor=white)](https://bsky.app/profile/nicolaounicos.bsky.social)
[![Dev.to blog](https://img.shields.io/badge/dev.to-0A0A0A?style=for-the-badge&logo=dev.to&logoColor=white)](https://dev.to/nicosnicolaou16)
[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)](https://www.youtube.com/@nicosnicolaou16)
[![Google Developer Profile](https://img.shields.io/badge/Developer_Profile-blue?style=for-the-badge&label=Google)](https://g.dev/nicolaou_nicos)

This project demonstrates how to implement a native Android Home Screen Widget within a **Flutter** application using **Jetpack Compose Glance**.

> [!IMPORTANT]  
> Check my article for the setup :point_right: [Android Widget Setup with Jetpack Compose Glance (with a Flutter example) - Medium](https://medium.com/@nicosnicolaou/android-widget-setup-with-jetpack-compose-glance-with-a-flutter-example-e07fb63c9466) :point_left: <br />

> [!IMPORTANT]
> Similar project with (Kotlin Language) :point_right: [AndroidWidgetWithCompose](https://github.com/NicosNicolaou16/AndroidWidgetWithCompose) :point_left: <br />

> [!IMPORTANT]
> NOTE: EXAMPLE FOR ANDROID ONLY. <br />

## ✨ Features

* **Modern Widget UI:** Uses Jetpack Compose Glance for building responsive app widgets.
* **Flutter Integration:** Bridges the gap between Flutter app data and native Android home screen components.
* **Material Support:** Includes dependencies for both Material 2 and Material 3 design systems.
* **Efficient Updates:** Uses `GlanceAppWidgetReceiver` for lifecycle management.

## 🛠️ Setup

### Step 1 add the follow dependencies libraries

```Kotlin
val composeGlanceWidgetVersion by extra("1.1.1")

dependencies {

    //...
    //Glance Widget
    implementation("androidx.glance:glance-appwidget:$composeGlanceWidgetVersion")
    //Using Material 2
    implementation("androidx.glance:glance-material:$composeGlanceWidgetVersion")
    //Using Material 3
    implementation("androidx.glance:glance-material3:$composeGlanceWidgetVersion")
}
```

### Steps 2 Create the Glance Receiver class that extend GlanceAppWidgetReceiver() and return the Widget Class

```Kotlin
class MyAppWidgetReceiver : GlanceAppWidgetReceiver() {
    override val glanceAppWidget: GlanceAppWidget
        get() = MyAppWidget()
}
```

### Step 3 Create the xml file into the xml directory (configuration to declare the size etc.)

```XML
<?xml version="1.0" encoding="utf-8"?>
<appwidget-provider xmlns:android="http://schemas.android.com/apk/res/android"
    android:initialLayout="@layout/glance_default_loading_layout" android:minWidth="250dp"
    android:minHeight="50dp" android:resizeMode="horizontal|vertical"
    android:widgetCategory="home_screen">
    
</appwidget-provider>
```

### Step 4 Register the Receiver Class into the Manifest and set the xml configuration for the Glance Widget

```XML

<receiver android:name=".glance_widget.receiver.MyAppWidgetReceiver" android:exported="true">
    <intent-filter>
        <action android:name="android.appwidget.action.APPWIDGET_UPDATE" />
    </intent-filter>
    <meta-data android:name="android.appwidget.provider"
        android:resource="@xml/my_app_widget_info" />
</receiver>
```

### Step 5 Create the Widget that extend GlanceAppWidget() class

```Kotlin
//...
class MyAppWidget : GlanceAppWidget() {

    override suspend fun provideGlance(context: Context, id: GlanceId) {
        provideContent {
            MyContent(context) //Compose UI
        }
    }
    //....
}
```

## 🔧 Versioning

* **Flutter SDK:** `3.42.4`
* **Dart Version:** `3.11.1`
* **Glance Version:** `1.1.1`

## 📚 References & Resources

* **Official Docs:** [Create an App Widget with Glance](https://developer.android.com/jetpack/compose/glance/create-app-widget)

## ⭐ Stargazers

If you enjoy this project, please give it a star!
Check out all the stargazers
here: [Stargazers on GitHub](https://github.com/NicosNicolaou16/Android_Widget_With_Compose_With_Flutter/stargazers)

## 🙏 Support & Contributions

This project is actively maintained. Feedback, bug reports, and feature requests are welcome! Please feel free to **open an issue** or submit a **pull request**.

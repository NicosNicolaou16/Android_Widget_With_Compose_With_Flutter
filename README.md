# android_widget_with_compose_with_flutter

This project is the setup for the Widget in Android with Jetpack Compose Glance in Flutter.

## Similar project with (Kotlin Language)

https://github.com/NicosNicolaou16/AndroidWidgetWithCompose <br />

## Step 1 add the follow dependencies libraries

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

## Steps 2 Create the Glance Receiver class that extend GlanceAppWidgetReceiver() and return the Widget Class

```Kotlin
class MyAppWidgetReceiver : GlanceAppWidgetReceiver() {
    override val glanceAppWidget: GlanceAppWidget
        get() = MyAppWidget()
}
```

## Step 3 Create the xml file into the xml directory (configuration to declare the size etc.)

```XML
<?xml version="1.0" encoding="utf-8"?>
<appwidget-provider xmlns:android="http://schemas.android.com/apk/res/android"
    android:initialLayout="@layout/glance_default_loading_layout" android:minWidth="250dp"
    android:minHeight="50dp" android:resizeMode="horizontal|vertical"
    android:widgetCategory="home_screen">
</appwidget-provider>
```

## Step 4 Register the Receiver Class into the Manifest and set the xml configuration for the Glance Widget

```XML

<receiver android:name=".glance_widget.receiver.MyAppWidgetReceiver" android:exported="true">
    <intent-filter>
        <action android:name="android.appwidget.action.APPWIDGET_UPDATE" />
    </intent-filter>
    <meta-data android:name="android.appwidget.provider"
        android:resource="@xml/my_app_widget_info" />
</receiver>
```

## Step 5 Create the Widget that extend GlanceAppWidget() class

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

## Check my article

https://medium.com/@nicosnicolaou/android-widget-setup-with-jetpack-compose-glance-with-a-flutter-example-e07fb63c9466  <br />

# Reference

https://developer.android.com/jetpack/compose/glance/create-app-widget  <br />

Flutter SDK version: 3.24.4 <br />
Dart Version: 3.5.4 <br />

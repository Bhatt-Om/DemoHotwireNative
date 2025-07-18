# 🚀 DemoHotwireNative

## 🔍 Definition

**Hotwire Native** = **Hotwire** + **Native Shell**

> It means using **Turbo Native** (Android/iOS) to load **HTML views** from your Rails app inside a **native mobile app** (via `WebView`), and still get:
- Smooth navigation  
- Real-time updates  
- Native mobile features

---

## 📊 Slide Content: What is Hotwire Native?

| Concept         | Description                                                              |
|-----------------|--------------------------------------------------------------------------|
| **Hotwire**      | HTML Over The Wire (send HTML, not JSON)                                |
| **Turbo**        | JS library that handles navigation and real-time updates                |
| **Turbo Native** | Lets you use Turbo inside native mobile apps                            |
| **Hotwire Native** | Combines backend HTML + Turbo + native mobile shell via WebView       |

---

## 📱 Key Android Concepts

| Android Term       | Meaning / Web Analogy                                                   |
|--------------------|-------------------------------------------------------------------------|
| **Activity**         | A full screen view (like a controller action or full-page view)        |
| **Fragment**         | A reusable UI block (like a partial or component)                      |
| **Intent**           | Navigation mechanism (like a redirect or route helper)                 |
| **WebView**          | Embedded browser to render HTML inside the app                         |
| **TurboActivity**    | Special `Activity` that handles Turbo Native navigation                |
| **TurboView**        | Renders HTML inside `TurboActivity` (like a `yield` in a layout)       |
| **Bridge Component** | Communicates between JS/HTML and Native (like Stimulus on Android)     |

---

## ⚙️ Rails Setup

1. Create a new Rails app with PostgreSQL and Tailwind CSS:

    ```bash
    rails new <app_name> -d=postgresql -c=tailwind
    ```

2. Prepare the database:

    ```bash
    rails db:prepare
    ```

3. Start the server:

    ```bash
    bin/dev
    # or
    rails s
    ```

4. Install Active Storage:

    ```bash
    rails active_storage:install
    ```

5. Generate a `Post` scaffold:

    ```bash
    rails generate scaffold Post title image:attachment like
    ```

6. Run migrations:

    ```bash
    rails db:migrate
    ```

---

## 📱 Native Android Setup

## 📱 Android Studio Setup

---

### 1. Create a New Project

- Open **Android Studio** and create a new project using the **"Empty Views Activity"** template.

![Create Project](./Hotwire%20Native%20Presentation/01.PNG)

---

### 2. Name Your Project

- Set your desired project name.

![Set Project Name](./Hotwire%20Native%20Presentation/02.PNG)

---

### 3. Change Folder View

- Switch the folder view to **Android** for a clearer project structure.

![Change to Android View](./Hotwire%20Native%20Presentation/03.PNG)

---

### 4. Add Turbo Native Dependencies

- Open `build.gradle.kts` (Module: app) under **Gradle Scripts**.

![Open Gradle File](./Hotwire%20Native%20Presentation/04.PNG)

- Add the following dependencies:

  ```kotlin
  dependencies {
      implementation("dev.hotwire:core:<latest-version>")
      implementation("dev.hotwire:navigation-fragments:<latest-version>")
  }


- Click Sync Project:
![Open Gradle File](./Hotwire%20Native%20Presentation/05.png)

### 5. Enable Internet Access
- In AndroidManifest.xml, add the following line above the <application> tag:

 ```kotlin
  <uses-permission android:name="android.permission.INTERNET"/>
```
- If you are using your localhost server than please insert this following line inside the < application > tag:

```kotlin
    android:usesCleartextTraffic="true"
```
### 6.Set Up Layout XML
- Open res/layout/activity_main.xml and replace the file with:

```kotlin
<?xml version="1.0" encoding="utf-8"?>
<androidx.fragment.app.FragmentContainerView
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/main_nav_host"
    android:name="dev.hotwire.navigation.navigator.NavigatorHost"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:defaultNavHost="false" />
```
### 7.Update MainActivity.kt
- Replace the contents of MainActivity.kt with the following:
```kotlin
import android.os.Bundle
import android.view.View
import androidx.activity.enableEdgeToEdge
import dev.hotwire.navigation.activities.HotwireActivity
import dev.hotwire.navigation.navigator.NavigatorConfiguration
import dev.hotwire.navigation.util.applyDefaultImeWindowInsets

class MainActivity : HotwireActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        enableEdgeToEdge()
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        findViewById<View>(R.id.main_nav_host).applyDefaultImeWindowInsets()
    }

    override fun navigatorConfigurations() = listOf(
        NavigatorConfiguration(
            name = "main",
            startLocation = "https://hotwire-native-demo.dev",
            navigatorHostId = R.id.main_nav_host
        )
    )
}
```

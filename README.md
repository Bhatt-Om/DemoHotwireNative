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

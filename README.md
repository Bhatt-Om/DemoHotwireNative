# DemoHotwireNative

Definition:
Hotwire Native = Hotwire + Native Shell
It means using Turbo Native (Android/iOS) to load HTML views from your Rails app inside a native app (via WebView), and still get navigation, real-time updates, and native features.

💡 Slide Content:
Hotwire ->	HTML Over The Wire (send HTML, not JSON)
Turbo ->	JS library that handles navigation, updates
Turbo Native ->	Tool that lets you use Turbo inside mobile apps
Hotwire Native ->	Combine your backend HTML + Turbo + native mobile shell


💡Slide Content: Key Android Concepts
Android Term	Meaning / Web Analogy
Activity	A full screen (like a controller action or full page)
Fragment	A reusable section of the screen (like a partial or component)
Intent	A way to navigate from one Activity to another (like a redirect or route helper)
WebView	A browser inside your app (renders HTML from server)
TurboActivity	A special Activity provided by Turbo Native to handle navigation using Turbo
TurboView	The part inside TurboActivity that loads the HTML (like yield in a layout)
Bridge Component	JS/HTML <--> Native communication tool (like Stimulus controller talking to Android)

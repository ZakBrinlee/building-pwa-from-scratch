# Frontend Masters Course - Building Progressive Web Apps from Scratch

## What will be covered
- Start with a web app
- Add Installation
- Set up Icons
- Enhance the UI
- Add a Service Worker
- Make an offline experience
- Installation Support
- App Store

## Questions
- Can the minimum window size be set?
-- No, PWA desktop does not allow the minimum window be set
- How do you know if a URL is a PWA?
-- Lighthouse tool
- How can the icon or theme color be updated?
-- Not a simple answer, depends on the platform
-- Android will trigger and update the next day
-- iOS/Desktop -> unable to update the icon/theme color

## Links
- [Web App Manifest](https://www.w3.org/TR/appmanifest/)
- [Test android on non-android devices](https://trygalaxy.com/) 
- [Maskable.app](https://maskable.app/) - App to help generate a maskable icon
- [Workbox](https://developer.chrome.com/docs/workbox/)
-- tool for service workers with large apps
- [BeforeInstallPRomptEvent](https://developer.mozilla.org/en-US/docs/Web/API/BeforeInstallPromptEvent)
- [PWA Builder](https://www.pwabuilder.com/) - Application to assist with building PWA components such as APK and Service Worker

## PWA
- Open Definition: not a complete/agreed upon defintion
- App build with web technologies
- Ability to work online or offline
- Installable
- Icon with standalone exp
- Ability to target Browser and Device
-- Able to become an APK for native mobile device and package for windows
- Brings together Web and Native universes together
- Web Univerise
-- Links and discoverability
-- Easy to deploy
-- Easy to update
-- Standards and tools (use what you are familiar with for web development)
- Native Device universe
-- Offline access
-- Installed icon and standalone
-- OS Integration
-- Performance and UX
- Flutter note
-- Multi-target solution
-- Compile to native packages for (android, ios, and PWA)
-- Need to use native design patterns
-- Unable to use HTML or CSS
- State of the PWA Platform
-- iOS-15 does not have support for push notifications
-- WebKit -> engine behind safari is working on the feature
-- May need native code if you publish in Apple App store
- PWA Support Mobile
- Android -> offline support
-- Chrome, Firefox, Opera, Edge, UC browser + some other one
- iOS
-- Safari
- iPadOS
-- Safari
- PWA Support Desktop
- ChromeBook
- Windows 10/11/7/8, MacOs, Linux
-- Chrome and Edge
- Offline Support
-- 93% offline support within a browser
-- 86% App exp within icon installation
- No Support
-- Android -> Facebook webview
-- iOS, iPadOS -> watch, webview chrome, fb, ff, opera, edge
-- windows, linux -> FF, Opera
-- macOS -> Safari, opera, FF
-- SmartTvs, smart watches, consoles, XR headsets 
- PWA Components
- Three main components
-- Web App
-- Web App Manifest
-- Service Worker

## Project
-- CodePad Masters -> stores notes while you are coding
-- Vanilla web app
-- No build process

## Start with a web app
- Standalone app
-- Window is owned by app. Navigation must be provided by app
- WebAPK on Android
-- Only if PWA Criteria passes
-- Full Android native package
-- Contains only app's name, Icon, URL
-- APK installed silently
-- Icon goes to homescreen and launcher
-- Google Chrome with Play Services
-- Samsung Internet on Samsung devices

## Set up Icons
- Recommended Sizes:
-- at least 192x192, 512x512
-- 384x384, 1024x1024
-- deprecated sizes: 72x72, 152x152
-- Simpler versions: 96x96, 
- Maskable icons
-- still square icon but with enough discardable padding to be in the safe area
-- Render a circle with a radius of 40%

## Enhance the UI
- Utilize CSS to handle device "safe-areas" UX
- Utilize Install/Share button
- Utilize media query with "display-mode" to handle different UX

## Add a Service Worker
- HTML registers a Service Worker
- SW installs CS resources
- Browser downloads resources on demand
- app consumes web services
- offline works
- Javascript file
-- Has it's own thread and acts as a middleware offering a local installed web server or web proxy for PWA including resources and API calls
-- Allows all the assests to be served from the client
- Runs client-side in browsers engine
- HTTPS required
- Installed by web page
- Own thread and lifecycle
- Acts as network proxy or local server in name of the real server
- Abilities to run in the Background
- No need for user's permission
- Scope -> SW can own the whole domain or only a folder in the scope
-- manages all pages within browser and within installed app from scope
- installed by any page in the scope
- it can serve all files requested from the scope
- only 1 sw is allowed per scope
- WebKit adds partition management
- SW has a local cache
- cache on request
- Common to follow an App Shell pattern
- Serving Resources
-- SW will respond for every request the PWA makes
-- It can serve from cache
-- it can forward request to network
-- it can synthesize a response
-- any mixed algorithm is possible
## Make an offline experience
- Any changes to the service worker, the user will get all the package again
- Updating Resources
-- Files are saved in the client
-- Updating files in the server won't trigger auto change in the client
-- We need to define and code and update algorithm
-- It will need a process within your build system for hasing and versioning files
- Developer is in full control of how to cache and serve the resouces of the PWA and manage API calls
- Updating the app doesn't require full installation
  
### Service Worker Lifecycle
- No service Worker -> parsed -> install -> waiting -> activating -> actived -> idle/stopped
-- actived with a fetch/push/message
-- idle after 40 seconds
-- actived again with another event
-- it might not be the same instance

## Installation Support
- Android testing -> devtools -> forward port
-  Install button
-  Share button

## App Store
- Distrubution Models
- Browser
- App Stores
-- MSFT store, Google Play store, Galaxy store
-- iOS (not direct but possible)
-- Enterprise distribution
- All dis models, we do not change how the app is installed and updated
- Service Worker is always the component responsible for managing assests
- Tools to create PWA Launchers
-- IDEs for native development (android studio, visual studio, xcode)
-- PWA Builder online tool (open source)
-- CLIs (playstores)
# Invoice_app
Invoice Application

Desktop Apps
Windows
macOS
Linux
Mobile Apps
iOS
Android
F-Droid
Dashboard View Invoice List Invoice New Invoice

Table of Contents
Setting up the app
Steps to remove non-FOSS code
Application Architecture
Package Structure
Blog Posts
Code generation
Tests
Code signing
Credits
Contributions
Setting up the app
Initialize the config file

cp lib/.env.dart.example lib/.env.dart

Support running the code unsigned on Android

cp android/app/build.gradle.dev android/app/build.gradle

Run the app

flutter run

Note: if you don't have an Invoice Ninja backend setup you can test the app with these credentials:

Email: demo@invoiceninja.com
Password: Password0
URL: demo.invoiceninja.com
Steps to remove non-FOSS code
cp android/build.gradle.foss android/build.gradle
cp lib/utils/oauth.dart.foss lib/utils/oauth.dart
cp lib/utils/app_review.dart.foss lib/utils/app_review.dart
cp lib/ui/app/upgrade_dialog.dart.foss lib/ui/app/upgrade_dialog.dart
cp lib/ui/app/pinput.dart.foss lib/ui/app/pinput.dart
cp android/app/src/main/AndroidManifest.foss.xml android/app/src/main/AndroidManifest.xml
cp pubspec.foss.yaml pubspec.yaml 
rm pubspec.lock
Application Architecture
The application was created using the Flutter Redux Starter.

The architecture is based off these two projects:

Redux Sample - Brian Egan
inKino - Iiro Krankka
File Structure
A High-level overview of the project structure:


lib/                     # Root Package
|
├─ data/                 # For data handling
│  ├─ mock/              # sample used for testing
│  ├─ models/            # Objects representing data
│  ├─ repositories/      # Source of data
|
├─ redux/                # manages app state
│  ├─ component/         # app building block
│     ├─ actions         # methods to update app state
|     ├─ middleware      # run in response to actions, execute before reducer
|     ├─ reducer         # intercepts actions, responsible for updating the state
|     ├─ selectors       # read data from the state, queries against your 'state database'
|     ├─ state           # immutable object that lives at the top of the widget hierarchy
|
├─ ui/                   # app views
│  ├─ component/         # views for different components
│    ├─ view/            # generel view for component
│    ├─ edit/            # change values on the views fields
|
├─ utils/                # Utility classes

The ui and redux folders contain components that are paired together. Put simply you will find an 'auth' folder in both the ui and redux folders.

For additional information on Redux architecture

Blog Posts
Intro to Google Flutter
Using Redux to manage state
Handling complex forms
Architectural review
Additional thoughts
Code generation
Run flutter packages pub run build_runner build --delete-conflicting-outputs to regenerate the model files. It will also remove the old generated files so conflicts are avoided..
Tests
Run flutter drive --target=test_driver/all_it.dart to run the tests
Code Signing
Run cp android/app/build.gradle.prod android/app/build.gradle to support running the code signed
Run cp android/key.properties.example android/key.properties to create the keys file
Run keytool -genkey -v -keystore key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias invoiceninja to generate a key to be able to sign the android application.
Update android/key.properties according to the parameters you entered in previous command when you generated the key
Open a new Firebase project from your console. Firebase is used for authentication.
Inside the project go to Authentication and enable at least one method.
After go to add a new Android application. For the package name add com.invoiceninja.flutter
Press "Register App" button.
Download "google-services.json" and put it in android/app directory.

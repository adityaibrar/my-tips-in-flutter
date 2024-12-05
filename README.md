# Tips & Trick Flutter

## How to set up the installation of Flutter SDK and Android SDK in Windows
1. Installation Flutter:
   1. Installation Flutter:
      - Open [Flutter Docs](https://flutter.dev/docs/get-started/install/windows.).
      - Download the latest version of the Flutter SDK file(ZIP).
   2. Extract Flutter SDK:
      - Extract the ZIP file to a permanent location such as ```D:\Android\flutter```.
   3. Add Flutter to PATH:
      - Open ```Control Panel → System → Advanced System Settings → Environment Variables```.
      - In “System variables,” find Path, click Edit, then add the ```flutter\bin``` folder location
        (example: ```D:\Android\flutter\bin```).
   4. Verification Installation
      - Open Command Prompt(CMD):
        ```bash
        flutter doctor
        ```
      - Make sure all statuses are displayed green. If any are red, follow the repair instructions.
2. Installation Android Studio:
   1. Download and Install:
      - Open [Android Studio](https://developer.android.com/studio.)
      - Download and install
   2. Add Android SDK:
      - Open Android Studio, then select ```More Actions → SDK Manager```.
      - Create a new folder in ```D:\Android``` named ```sdk``` as below
        ```makefile
        D:\Android\sdk
        ```
      - Select the latest version of the SDK, check ```Android SDK Platform-Tools```, and click **Apply** to download.
   3. Add Android SDK to PATH
      - Open ```Control Panel → System → Advanced System Settings → Environment Variables```.
      - Create new variable named ```ANDROID_HOME``` then fill in the value in the value variable
        (example:```D:\Android\sdk```).
      - Click ```Path``` then create new path ```D:\Android\sdk```, click **OK**.
   4. Verification Installation
      - run ```flutter doctor``` to make sure flutter recognizes Android Studio. 
3. Installation JDK (Java Development Kit):
   1. Download and Install:
      - Open [JDK](https://www.oracle.com/java/technologies/javase-downloads.html)
      - Download and install
   2. Add Android SDK to PATH
      - Open ```Control Panel → System → Advanced System Settings → Environment Variables```
      - Create new variable named ```JAVA_HOME``` then fill in the value in the value variable (example:```C:\Program Files\Java\jdk-<version>```)
      - Click ```Path``` then create new path ```%JAVA_HOME%\bin```, click **OK**
   3. Verification Installation
      - Open Command Prompt(CMD):
        ```bash
        java -version
        ```
      - If the JDK is installed correctly, the Java version information will appear.
4. Installation Gradle:
   1. Download and Install:
      - Open [Gradle](https://gradle.org/releases/.)
      - Download and install
   2. Extract Gradle:
      - Extract the ZIP file to a permanent location such as ```C:\gradle```.
   3. Add Flutter to PATH:
      - Open ```Control Panel → System → Advanced System Settings → Environment Variables```.
      - In “System variables,” find Path, click Edit, then add folder location
        (example: ```C:\gradle\bin```).
   4. Verification Installation
      - Open Command Prompt(CMD):
        ```bash
        gradle -v
        ```
      - Make sure version gradle appears.

and the last step we run the command ```flutter doctor``` to make sure flutter recognize Android Studio, JDK, and Gradle correctly.

>[!IMPORTANT]
>cmdline-tools component missing

if you having problems like this, You can open the android studio application selece ```SDK Manager → SDK Tools``` and click ```Android SDK Command-line Tools (latest)```, and **Apply**.

>[!IMPORTANT]
>Run `flutter doctor --android-licenses` to accept the SDK Licenses

you can running this command:
```sh
flutter doctor --android-licenses
```
 and Y for accept/ n for not.

## How to delete flutter native splash screen 

1. open this file ```launch_background.xml```:
    ```sh
      android/app/src/main/res/drawable/launch_background.xml
    ```
    Fill the file with empty elements like this:
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <layer-list xmlns:android="http://schemas.android.com/apk/res/android">
        <!-- Delete Flutter icon in here -->
    </layer-list>
    ```
2. check file ```styles.xml```:
   ```sh
   android/app/src/main/res/values/styles.xml
   ```
   Make sure the splash screen is not referenced. If there is a reference to ```launch_background```, change it to an empty theme like this:
   ```xml
   <style name="LaunchTheme" parent="@android:style/Theme.Black.NoTitleBar">
   </style>

   ```
3. Delete ```android:windowBackground``` from Manifext:
   open this file:
   ```sh
   android/app/src/main/AndroidManifest.xml
   ```
   remove the following attributes if present:
   ```xml
   android:theme="@style/LaunchTheme"
   ```
   Make sure ```@style/LaunchTheme``` is not used as the theme for the main activity.
   
   

# Install and Deploy Flutter

## Get the Flutter SDK  

Select the operating system on which you are installing Flutter:

+ [Windows](#windows)
+ [macOs](#macos)
+ [Linux](#linux)

### **Windows**

Download the latest [flutter SDK](https://flutter.dev/docs/development/tools/sdk/releases?tab=windows)

#### **Update your path**

If you wish to run Flutter commands in the regular Windows console, take these steps to add Flutter to the PATH environment variable:

+ From the Start search bar, enter ‘env’ and select Edit environment variables for your account.
+ Under User variables check if there is an entry called Path:
  + If the entry exists, append the full path to flutter\bin using ; as a separator from existing values.
  + If the entry doesn’t exist, create a new user variable named Path with the full path to flutter\bin as its value.
  
Note that you have to close and reopen any existing console windows for these changes to take effect.

### **macOs**

Download the latest [flutter SDK](https://flutter.dev/docs/development/tools/sdk/releases?tab=macos)

#### **Update your path**  

Add the flutter tool to your path:

1. Determine the directory where you placed the Flutter SDK. You need this in Step 3.
2. Open (or create) the rc file for your shell. For example, macOS Mojave (and earlier) uses the Bash shell by default, so edit $HOME/.bash_profile or $HOME/.bashrc. macOS Catalina uses the Z shell by default, so edit $HOME/.zshrc. If you are using a different shell, the file path and filename will be different on your machine.

3. Add the following line and change [PATH_TO_FLUTTER_GIT_DIRECTORY] to be the path where you cloned Flutter’s git repo:  

    ```bash
    export PATH="$PATH:[PATH_TO_FLUTTER_GIT_DIRECTORY]/flutter/bin"
    ```

4. Run source $HOME/.<rc file\> to refresh the current window, or open a new terminal window to automatically source the file.
5. Verify that the flutter/bin directory is now in your PATH by running:  

    ```bash
    echo $PATH
    ```

    Verify that the flutter command is available by running:

    ```bash
    which flutter
    ```

### **Linux**

Download the latest [flutter SDK](https://flutter.dev/docs/development/tools/sdk/releases?tab=linux)

#### **Update your path**

Add the flutter tool to your path:

1. Determine the directory where you placed the Flutter SDK. You need this in Step 3.
2. Open (or create) the rc file for your shell. For example, macOS Mojave (and earlier) uses the Bash shell by default, so edit $HOME/.bash_profile or $HOME/.bashrc. macOS Catalina uses the Z shell by default, so edit $HOME/.zshrc. If you are using a different shell, the file path and filename will be different on your machine.

3. Add the following line and change [PATH_TO_FLUTTER_GIT_DIRECTORY] to be the path where you cloned Flutter’s git repo:  

    ```bash
    export PATH="$PATH:[PATH_TO_FLUTTER_GIT_DIRECTORY]/flutter/bin"
    ```

4. Run source $HOME/.<rc file\> to refresh the current window, or open a new terminal window to automatically source the file.
5. Verify that the flutter/bin directory is now in your PATH by running:  

    ```bash
    echo $PATH
    ```

    Verify that the flutter command is available by running:

    ```bash
    which flutter
    ```

## **Run flutter doctor**

Run the following command to see if there are any dependencies you need to install to complete the setup (for verbose output, add the -v flag):

```bash
flutter doctor
```

This command checks your environment and displays a report to the terminal window. The Dart SDK is bundled with Flutter; it is not necessary to install Dart separately. Check the output carefully for other software you might need to install or further tasks to perform (shown in **bold** text).

For example:

```
[-] Android toolchain - develop for Android devices
    • Android SDK at /Users/obiwan/Library/Android/sdk
    ✗ Android SDK is missing command line tools; download from https://goo.gl/XxQghQ
    • Try re-installing or updating your Android SDK,
      visit https://flutter.dev/setup/#android-setup for detailed instructions.
```

The following sections describe how to perform these tasks and finish the setup process. Once you have installed any missing dependencies, you can run the flutter doctor command again to verify that you’ve set everything up correctly.

## Install Android Studio

1. Download and install [Android Studio](https://developer.android.com/studio).

2. Start Android Studio, and go through the ‘Android Studio Setup Wizard’. This installs the latest Android SDK, Android SDK Command-line Tools, and Android SDK Build-Tools, which are required by Flutter when developing for Android.

## Set up your Android device

To prepare to run and test your Flutter app on an Android device, you’ll need an Android device running Android 4.1 (API level 16) or higher.

1. Enable Developer options and USB debugging on your device. Detailed instructions are available in the [Android documentation](https://developer.android.com/studio/debug/dev-options).

2. Windows-only: Install the [Google USB Driver](https://developer.android.com/studio/run/win-usb).

3. Using a USB cable, plug your phone into your computer. If prompted on your device, authorize your computer to access your device.

4. In the terminal, run the <span style="color:#008f83">flutter devices</span> command to verify that Flutter recognizes your connected Android device. By default, Flutter uses the version of the Android SDK where your <span style="color:#008f83">adb</span> tool is based. If you want Flutter to use a different installation of the Android SDK, you must set the <span style="color:#008f83">ANDROID_HOME</span> environment variable to that installation directory.

## **Build the application**

+ Clone latest version from Github:

    ```bash
    git clone https://github.com/IBM-AR-CARD/Flutter-AR-Mobile-App.git
    ```

+ Make sure you current dirctory is **Flutter-AR-Mobile-App**

### Run it on your phone

1. in order to get latest flutter package. Run the following command:

    ```bash
    flutter pub get
    ```  

2. Connect to your phone into computer.

3. run:

    ```bash
    flutter run
    ```

    To install the application into your phone

### Build the project to apk

in order to get latest flutter package. Run the following command:

```bash
flutter pub get
```  

To build the project into apk:

```bash
flutter build apk --profile
```  

if success you will see the follow output:

```bash
√ Built build\app\outputs\apk\release\app-release.apk (303.2MB).
```

which specifies the location of the application. 

*Instruction reference from <https://flutter.dev/docs/get-started/install>*

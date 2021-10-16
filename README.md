# React-Native-Environment-Setup-in-Ubuntu

This documentation will help you install and build your first app in React Native.
### Note: This documentation is for Ubuntu users.

## Installing Dependencies

You will need Node, React Native Command Line Interface, a JDK, Android studio and also an Editor of your choice.

## Node

Step1: Open your terminal or press `Ctrl+Alt+T`

Step2: Type the following Command: `sudo apt install node.js`

Step3: Once It is installed, Verify it by checking the installed version using the following command: `node -v` or `node -version`

##### Or You can follow the [Installation instruction for your Linux distribution](https://nodejs.org/en/download/package-manager/) to install node.

## Java Development Kit

React Native require atleat version 8 of JDK. Install the JDK in the following manner:
Step1: Open the terminal `(Ctrl+Alt+T)` and update the package repository to ensure you download the latest version using the following command: `sudo apt update`

Step2: Install the Java Development Kit by using following command: `sudo apt install openjdk-8-jdk`

Step3: Confirm the installation by typing `Y(yes)` and press `Enter`

Step4: Verify the version of Java with the command: `java -version`

##### Or You can download and install [OpenJDK](https://openjdk.java.net/) from [AdoptOpenJDK](https://adoptopenjdk.net/) .

#### How to set Java_Home Environment Variables:

Step1: To setup the Java_Home variable, you first need to find where java is installed. Use the following command to locate it: `sudo update-alternatives --config java`

Step2: Once you see all the paths, Copy one of your preferred Java Version and Open `/etc/environment/` file. At the end of the file add a line which specifies the location of JAVA_HOME in the following manner: `JAVA_HOME="/your/installation/path/"`

## Android Development Environment

If you're new to Android Development then follow the following step carefully:

#### 1.Install Android Studio 

Download and Install [AndroidStudio](https://developer.android.com/studio). While on Android Studio installation wizard, make sure the boxes next to all of the following items are checked:

=> **`Android SDK`**

=> **`Android SDK Platform`**

=> **`Android Virtual Device`**

Then, click "Next" to install all of these components.

Once setup has finalized and you're presented with the Welcome screen, proceed to the next step.

***Note:If the checkboxes are grayed out, you will have a chance to install these components later on.***

#### 2.Install the Android SDK

Android Studio installs the latest Android SDK by default. Building a React Native app with native code, however, requires the Android 10 (Q) SDK in particular. Additional Android SDKs can be installed through the SDK Manager in Android Studio.

To do that, open Android Studio, click on "Configure" button and select "SDK Manager".

Select the "SDK Platforms" tab from within the SDK Manager, then check the box next to "Show Package Details" in the bottom right corner. Look for and expand the `Android 10 (Q)` entry, then make sure the following items are checked:

=> `Android SDK Platform 29`
=> `Intel x86 Atom_64 System Image` or `Google APIs Intel x86 Atom System Image`

Next, select the "SDK Tools" tab and check the box next to "Show Package Details" here as well. Look for and expand the "Android SDK Build-Tools" entry, then make sure that `29.0.2` is selected.

Finally, click "Apply" to download and install the Android SDK and related build tools.

#### 3. Configure the ANDROID_HOME environment variable

The React Native tools require some environment variables to be set up in order to build apps with native code.

Add the following lines to your `$HOME/.bash_profile` or `$HOME/.bashrc` (if you are using `zsh` then `~/.zprofile` or `~/.zshrc`) config file:

`export ANDROID_HOME=$HOME/Android/Sdk`
`export PATH=$PATH:$ANDROID_HOME/emulator`
`export PATH=$PATH:$ANDROID_HOME/tools`
`export PATH=$PATH:$ANDROID_HOME/tools/bin`
`export PATH=$PATH:$ANDROID_HOME/platform-tools`

***Note: `.bash_profile` is specific to bash. If you're using another shell, you will need to edit the appropriate shell-specific config file.***

Type `source $HOME/.bash_profile` for `bash` or `source $HOME/.zprofile` to load the config into your current shell. Verify that ANDROID_HOME has been set by running `echo $ANDROID_HOME` and the appropriate directories have been added to your path by running `echo $PATH`.

***Note: Please make sure you use the correct Android SDK path. You can find the actual location of the SDK in the Android Studio "Preferences" dialog, under Appearance & Behavior → System Settings → Android SDK.***

## React Native Command Line Interface

React Native has a built-in command line interface. Rather than install and manage a specific version of the CLI globally, we recommend you access the current version at runtime using `npx`, which ships with Node.js. With `npx react-native <command>`, the current stable version of the CLI will be downloaded and executed at the time the command is run.

## Creating a new application

Let's create a new React Native project naming "Hello React" by typing the following command : `npx react-native init AwesomeProject`

## Preparing the Android device

You will need an Android device to run your React Native Android app. This can be either a physical Android device, or more commonly, you can use an Android Virtual Device which allows you to emulate an Android device on your computer.

## Using a Physical Device

If you have a physical Android device, you can use it for development in place of an AVD by plugging it in to your computer using a USB cable and following the instructions here.

**1.Enable Debugging over USB**

You will need to enable USB Debugging on your device in order to install your app during development.

To enable USB debugging on your device, you will first need to enable the `Developer options` menu by going to `Settings` → `About phone` → `Software information` and then tapping the `Build number` row at the bottom seven times. You can then go back to `Settings` → `Developer options` to enable `USB debugging`.

Now check that your device is properly connecting to ADB, the Android Debug Bridge, by running `adb devices`.

## Run your App

Type the following in your command prompt to install and launch your app on the device:

`$ npx react-native run-android`

## Connecting to the development server

You can also iterate quickly on a device by connecting to the development server running on your development machine. There are several ways of accomplishing this, depending on whether you have access to a USB cable or a Wi-Fi network.

**Method 1: Using adb reverse (recommended)**

If your device has USB debugging enabled, and it is connected via USB to your development machine.

Run the following in a command prompt:

`$ adb -s <device name> reverse tcp:8081 tcp:8081`

To find the device name, run the following adb command:

`$ adb devices`

**Method 2: Connect via Wi-Fi**

You can also connect to the development server over Wi-Fi. You'll first need to install the app on your device using a USB cable, but once that has been done you can debug wirelessly by following these instructions. You'll need `your development machine's current IP address` before proceeding.

Open a terminal and type `/sbin/ifconfig` to find your machine's IP address.

1. Make sure your laptop and your phone are on the same Wi-Fi network.
2. Open your React Native app on your device.
3. You'll see a red screen with an error. This is OK. The following steps will fix that.
4. Open the in-app `Developer menu`.
5. Go to `Dev Settings` → `Debug server host & port for device`.
6. Type in your machine's IP address and the port of the local dev server (e.g. 10.0.1.1:8081).
7. Go back to the `Developer menu` and select `Reload JS`.

You can now enable Live reloading from the `Developer menu`. Your app will reload whenever your JavaScript code has changed.

## Running your React Native application

**Step 1: Start Metro**

To start Metro, run `npx react-native start` inside your React Native project folder.

***Note: If you use the Yarn package manager, you can use yarn instead of npx when running React Native commands inside an existing project.***

**Step 2: Start your application**

Open a new terminal inside your React Native project folder. Run the following:

`npx react-native run-android`

**Modifying your app**

Now that you have successfully run the app, let's modify it.

=> Open `App.js` in your text editor of choice and edit some lines.

=> Press the `R` key twice or select Reload from the Developer Menu (Ctrl + M) to see your changes!

**That's it!**

Congratulations! You've successfully run and modified your first React Native app.


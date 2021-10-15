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

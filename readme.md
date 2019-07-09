### 移动端开发环境搭建(Mac)

- 版本：v.1.0.0

- 说明: 本文档主要用于 macOS 用户快速搭建项目开发环境

#### 准备工具

安装下面这些工具，以确保可以得到更好的开发体验：

<font color=#0099ff size=3>git</font>：请前往网址：https://git-scm.com/download/mac 进行下载, 安装完成后需要使用简单的命令配置用户的 id，email，具体操作如下所示： 

 `git config --global user.name "Your Name"`
 `git config --global user.email "email@example.com"`

或者直接在终端里面输入 git，点击回车键(enter) 进行安装。

<font color=#38f size=3>ssh client</font>：比如 PuTTy, 用于安全登录 ionic Appflow。

<font color=#38f size=3>node.js</font>：首先确保安装了 node.js, 用 `node -v` 指令来查看，如果还没有安装，可以到地址 https://nodejs.org 进行安装。

<font color=#38f size=3>代码编辑器</font>：推荐使用 Visual Studio Code, 如果还没有安装，请到地址 https://code.visualstudio.com/ 进行下载，可以根据自己的喜好进行一些简单的配置。

<font color=#38f size=3>命令行终端(cli)</font>：可以用 mac 自带的终端，其他终端工具推荐使用 iterm2。

### 安装 cordova 和 ionic 

运行下面的命令：

`$ npm install -g cordova ionic`

如果已经安装，确保更新到最新的版本，使用下面的命令

`sudo npm update -g cordova ionic`

创建一个应用

在系统合适的目录下，使用我们的 “tabs” 应用模板创建一个 ionic angular 应用：

`ionic start myApp tabs`

创建成功后，使用命令 cd myApp 目录下，执行命令 `ionic serve`, 或者执行 `ionic serve -l` (带热更新)会自动打开流量器显示页面。

### angular + ionic Framework

在 Angular 项目中使用 Ionic Framework 时，请从 npm 安装最新的 @ionic / angular 软件包。这包含所有 Ionic Framework 组件和 Angular 特定服务和功能。

`$ npm install @ionic/angular@latest --save`

### android 安装程序

要定位 android 平台，需要一些额外的环境设置。可以在 Windows，macOS 和 Linux上创建 Android 应用程序。

java

原生 Android 应用程序使用 Java 编程语言编译, 从下载页面 https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html JDK8。

温馨提示：Cordova 与最新版本的 Java 不兼容。您必须安装 JDK8 才能使用 Cordova 构建 Android 应用程序。

gradle

Gradle 是 Android 应用中使用的构建工具，必须单独安装。有关详细信息，请参阅安装页面 https://gradle.org/install/ 进行安装。

Android Studio

Android Studio 是用于创建原生 Android 应用程序的 IDE。它包括 Android SDK，需要配置它才能在命令行中使用。Android Studio 还用于创建 Android 虚拟设备，这是 Android 模拟器所必需的。应用程序也可以启动到设备。请参阅安装页面 https://developer.android.com/studio/ 进行安装。

安装 Android SDK

安装完成后，打开 Android Studio，IDE 应检测到需要安装 Android SDK。在 SDK Components Setup 屏幕中，完成 SDK 的安装。记下 Android SDK 位置。默认情况下，安装了最新的稳定 SDK 平台，其中包含针对该版本 Android 所需的一组软件包。Android SDK 可以在 Android Studio 欢迎界面的 Configure > SDK Manager 菜单中使用 Android Studio 进行管理，也可以在 Android 项目中使用 Tools > SDK Manager 进行管理。

配置系统环境变量

Android SDK 附带了有用的命令行工具，在使用它们之前，必须设置一些环境变量。在〜/ .bashrc，〜/ .bash_profile 或类似的 shell 启动脚本中，进行以下修改：

设置 ANDROID_SDK_ROOT 环境变量。此路径应为上一节中使用的 Android SDK 位置。

`$ export ANDROID_SDK_ROOT=$HOME/Library/Android/sdk`

将 Android SDK命令行目录添加到 PATH。每个目录对应于命令行工具的类别。

`# avdmanager, sdkmanager`
`export PATH=$PATH:$ANDROID_SDK_ROOT/tools/bin`

`# adb, logcat`
`export PATH=$PATH:$ANDROID_SDK_ROOT/platform-tools`

`# emulator`
`export PATH=$PATH:$ANDROID_SDK_ROOT/emulator`

### 创建一个安卓虚拟设备

AVD 由 AVD Manager 管理。在 Android Studio 欢迎屏幕中，单击 config> AVD 管理器。AVD Manager 也可以在 Tools > AVD Manager 菜单中的 Android 项目中打开。单击 “create cirtual device” 并选择合适的设备定义。 如果不确定，请选择 Pixel 2. 然后，选择合适的系统映像。如果不确定，请选择带有 Google Play 服务的 Pie（API 28）。有关 Android 版本的信息，请参阅 Android 版本历史记录。创建 AVD 后，将 AVD 启动到 Android 模拟器中。保持模拟器运行是确保在开发 Android 的 Ionic 应用程序时检测的最佳方法。

### 设置安卓设备

在设备上启用 USB 调试。打开设置，导航到开发者选项，然后启用 USB 调试。可能需要首先启用 “开发者选项” 菜单。确保设备有权连接到计算机。对于 macOS，无需其他设置。通过设备数据线将设备连接到计算机并使用以下命令验证连接是否正常：
`adb install -r xxx.apk `
`$ adb devices`

有关故障排除和详细信息，请参阅 https://developer.android.com/studio/command-line/adb 进行纠错。

### ios 设置

要定位 iOS，需要一些其他环境设置。不幸的是，iOS 应用程序只能在 macOS 上创建。

Xcode

Xcode 是用于创建本机 iOS 应用程序的 IDE。它包括iOS SDK 和 Xcode 命令行工具。可以使用 Apple 帐户免费下载 Xcode（https://developer.apple.com/download/）, 也可以通过 App Store 安装。

创建一个开发团队

所有iOS应用程序都必须经过代码签名，即使是开发。幸运的是，Xcode 通过自动代码签名使这一切变得简单。唯一的先决条件是 Apple ID。打开 Xcode 并导航到 Xcode > Preference > Accounts。 如果没有列出，请添加 Apple ID。 登录后，个人团队将出现在 Apple ID 的团队列表中。

创建 ios 模拟器

iOS 模拟器在 Mac 上模拟 iOS 设备，打开 Xcode 并导航到 Window > Devices and Simulators。创建一个 iPhone X 模拟器。

ios-sim & ios-deploy 

`sudo npm install -g ios-sim`

添加 ios 平台，编译，模拟器运行

ios-sim 和 ios-deploy 是在开发过程中将应用程序部署到 iOS 模拟器和 iOS 设备的实用程序。它们可以使用 npm 全局安装。
 
`$ npm install -g ios-sim`
`$ npm install -g ios-deploy`

### 添加平台(平台可以是 android，ios)

进入项目所在文件夹，在命令提示符中，执行添加平台命令。

`ionic cordova platform add $platform`

### 真机运行

`ionic cordova run $platform --prod`

### 在手机中调试

在开发时，开启热更新，并在命令提示符中打印应用和开发服务器日志，使用下面的命令：

`ionic run android -l -c –s `

### 打包程序

`ionic cordova build $platform --release --prod`



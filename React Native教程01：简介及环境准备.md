
 > 本教程适合已有React开发经验的朋友阅读哦~

## 移动端开发方式

目前移动端开发方式主要分为4种，分别为Web、原生、混合、编译开发。React Native就是属于编译型开发，即将JavaScript编译成原生代码，实际生成的还是原生APP。

对比一下几种开发方式的优缺点：

|  | Web | 原生 | 混合 | 编译 |
|--|--|--|--|--|
| 能否跨平台 | 能 | 不能 | 能 | 能 |
| 调用系统权限 | 不能 | 能 | 能 | 能 |
| 开发便利性 | 好 | 差 | 好 | 好 |
| 性能 | 差 | 好 | 差 | 好 |
| 开发框架、插件等 | 丰富 | 丰富 | 丰富 | 较少 |

从以上对比可以看出，编译型开发方式相比其他开发方式有很大优势，但缺点就是还不够成熟。

## React Native简介

 1. React Native不是网页开发，HTML标签和CSS样式都无法使用，但提供了React Native组件和替代样式，让开发者可以用类似于网页开发的方式，进行原生应用开发。
 2. React和JavaScript（ES6）几乎完全支持，当然JavaScript最终会被编译成原生代码。

## React Native环境准备

 1. 安装Android Studio（需要科学上网，安装流程可以参考：[https://www.cnblogs.com/xiadewang/p/7820377.html](https://www.cnblogs.com/xiadewang/p/7820377.html)），Mac系统还需要安装xcode。
 2. 安装包管理工具：yarn，可以设置淘宝镜像：yarn config set registry 'https://registry.npm.taobao.org'，以提升安装速度。
 3. 安装JDK1.8（参考：[https://blog.csdn.net/u014166319/article/details/71791287](https://blog.csdn.net/u014166319/article/details/71791287)）。
 4. 安装Android SDK：Android 8.1（API Level27）。
 5. 安装Android SDK Tools：Android Emulator。
 6. 添加环境变量：变量名ANDROID_HOME，变量值为Android SDK地址。
 7. 安装react-native-cli工具：npm i -g react-native-cli。

## 新建React Native项目

1. 使用react-native init project-name就可以创建一个新的React Native项目，会自动通过yarn安装依赖。
2. 通过Android Studio中的Android Virtual Device Manager创建一个设备并启动。
3. 依赖安装完成后，通过react-native run-android就可以启动React Native项目。
a. 在Mac中若遇到报错：Error: `fsevents` unavailable (this watcher can only be used on Darwin)，可以参考[https://github.com/expo/expo/issues/854](https://github.com/expo/expo/issues/854)。
需要先安装xcode并且同意协议，然后安装brew：https://brew.sh/，最后运行npm r -g watchman和brew install watchman命令即可。
b. 在Mac中若出现报错：SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable。则可以在工程的根目录下的android文件下新建一个local.properties的文件，在文件中写入sdk.dir=你的sdk目录。参考：[https://www.jianshu.com/p/c04ac43f5021](https://www.jianshu.com/p/c04ac43f5021)
c. 在Mac中若出现报错：adb: command not found。则需要配置配置Android环境变量，参考：[https://www.jianshu.com/p/db3298ca0a32](https://www.jianshu.com/p/db3298ca0a32)

4. 启动过程中会弹出一个Android 调试桥 (adb) 的命令行工具，它是用于连接Android设备并进行通信。
5. 编译完成之后，React Native项目会自动在Android设备中弹出，这时可以看到一个欢迎页面。
6. 在Mac中运行一个iOS项目，需要先安装xcode，之后运行react-native run-ios就可以在模拟器中查看到React Native项目。

接下来就可以愉快地开始React Native开发了。
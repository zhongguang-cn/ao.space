# 简介

客户端为傲空间的交互入口，让用户可在不同平台上快速安全的访问个人数据。傲空间客户端支持Android、iOS、web平台，提供了扫码绑定、授权登录、文件管理、系统升级、平台环境切换等功能。

## Android app 编译构建

### 环境准备

* 安装 Java 开发工具包 (JDK)，配置 JAVA_HOME 环境变量
* 下载并安装 Android Studio 开发工具，在安装过程中，选择安装 Android SDK 和其他必要的组件
* 创建 Android 虚拟设备（AVD），或使用Android系统手机，打开开发者选项，连接开发设备

### 源码下载

可以使用[项目整体下载](xxx)下载的方式，也可以通过通过一下命令下载本模块的仓库：

* `git clone git@github.com:ao-space/space-aofs.git ./client-android`

### 部署

使用 Android Studio 导入 client-android 项目。可在点击 `Run app` 直接在虚拟设备/真机上运行、调试项目。也可通过点击 `Build - Generate Signed Bundle or APK` ，选择 APK ， 使用自己创建的密钥库文件进行签名打包，以安装包的形式安装到Android系统手机上。

## ios app 编译构建

### 环境准备

准备好 docker环境

### 源码下载

可以使用[项目整体下载](xxx)下载的方式

### 容器镜像构建

进行服务器整体容器镜像的构建，可以逐个描述，也可以提供一个脚本，一次性构建。

### 部署

描述服务器部署，包括官方发布的镜像和自行构建的镜像两种部署方式

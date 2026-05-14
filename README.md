# 硬件导师 - Android App

硬件工程师学习平台移动应用

## 项目简介

这是一个基于WebView的Android应用，将硬件工程师学习平台打包成原生Android APK。

## 功能特性

- 📚 完整的硬件工程知识体系
- 🔍 搜索和收藏功能
- 📱 移动端优化界面
- 🌐 离线访问（所有内容打包在APK中）

## 项目结构

```
.
├── app/
│   └── src/main/
│       ├── java/com/hardware/mentor/MainActivity.java
│       ├── res/layout/activity_main.xml
│       ├── assets/hardware-mentor-complete.html
│       └── AndroidManifest.xml
├── build.gradle
├── gradlew / gradlew.bat
└── .github/workflows/build.yml
```

## 自动编译（GitHub Actions）

每次push代码到main/master分支，GitHub Actions会自动：
1. 编译Debug版本APK
2. 编译Release版本APK
3. 上传APK作为Artifacts（保留30天）

### 下载编译好的APK

1. 进入项目的 [Actions](../../actions) 页面
2. 点击最新的构建记录
3. 在底部找到 "Artifacts" 区域
4. 下载 `hardware-mentor-debug-apk` 或 `hardware-mentor-release-apk`

## 手动编译

### 前提条件
- JDK 17 或更高版本
- Android SDK

### 编译步骤

```bash
# 克隆项目
git clone https://github.com/你的用户名/hardware-mentor.git
cd hardware-mentor

# 授权gradlew
chmod +x gradlew  # Linux/Mac
# 或
# gradlew.bat  # Windows

# 编译Debug版本
./gradlew assembleDebug

# 编译Release版本
./gradlew assembleRelease

# APK生成位置
# Debug: app/build/outputs/apk/debug/app-debug.apk
# Release: app/build/outputs/apk/release/app-release-unsigned.apk
```

## 安装到手机

1. 启用"未知来源"安装权限
   - 设置 → 安全 → 未知来源（启用）
   
2. 传输APK到手机并安装

3. 或使用adb安装：
```bash
adb install app/build/outputs/apk/debug/app-debug.apk
```

## 技术栈

- **开发环境**: Android Studio / AIDE
- **编译工具**: Gradle 7.5
- **Android SDK**: API 30 (Android 11)
- **最低支持**: API 16 (Android 4.1)
- **WebView**: 加载本地HTML文件

## 常见问题

### Q: HTML文件可以更新吗？
A: 可以。修改 `app/src/main/assets/hardware-mentor-complete.html` 后重新编译即可。

### Q: 如何更换应用图标？
A: 替换 `app/src/main/res/mipmap-*/ic_launcher.png` 文件。

### Q: 如何修改应用名称？
A: 编辑 `app/src/main/res/values/strings.xml` 中的 `app_name`。

## 许可证

MIT License

## 联系方式

如有问题，请提交Issue。

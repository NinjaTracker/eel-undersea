# 海鳗小勇士（安卓版工程）

整个游戏在 `app/src/main/assets/index.html` 里，安卓部分只是一个全屏外壳（`MainActivity.java`）。

## 方法一：用 GitHub 在线打包（不用装任何软件）
1. 登录 github.com，新建一个仓库（Private 也可以）。
2. 点 “uploading an existing file”，把这个文件夹里的**所有内容**拖进去（包括 `.github` 文件夹），提交。
   - 如果网页上拖不进 `.github` 文件夹：在仓库里点 Add file → Create new file，文件名填 `.github/workflows/build-apk.yml`，把本工程里同名文件的内容粘贴进去。
3. 打开仓库的 **Actions** 页，等 “Build APK” 变成绿色对勾（约 3–5 分钟）。
4. 点进这次运行，在底部 **Artifacts** 下载 `MorayEel-apk`，解压得到 `app-release.apk`。

## 方法二：用 Android Studio
1. 安装 Android Studio，选择 Open 打开本文件夹，等待同步完成。
2. 菜单 Build → Build App Bundle(s) / APK(s) → Build APK(s)。
3. APK 在 `app/build/outputs/apk/` 下。

## 安装到手机
把 APK 传到手机，点开安装；第一次会提示“允许安装未知来源应用”，允许即可。

## 修改游戏
直接改 `assets/index.html` 再重新打包。每次重新打包后版本号可在 `app/build.gradle` 的 `versionCode` 里 +1。
注意：用 GitHub 打包时每次签名证书可能不同，覆盖安装失败的话先卸载旧版本再装（设置会被清空）。

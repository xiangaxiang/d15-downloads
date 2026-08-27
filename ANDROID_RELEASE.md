# Android 发布入口与操作步骤

这个文件放在下载中心仓库根目录，专门记录 Android 安装包的固定位置和发布方法。以后不需要从历史对话里找链接。

## 最常用的两个固定链接

### 发给用户下载

<https://gitee.com/d15cyber/d15-downloads/releases/download/android-latest/D15Guitar-Android-latest.apk>

这个地址和现有二维码保持不变。用户下载后直接覆盖安装，不要先卸载旧版，否则可能丢失本机数据。

### 自己替换最新版

<https://gitee.com/d15cyber/d15-downloads/releases/android-latest/edit>

这个页面需要登录 Gitee。它用于删除旧 APK 附件、上传新 APK，并点击“更新”完成发布。

建议把以上两个链接分别收藏为：

- `D15 Android 用户下载`
- `D15 Android 发布管理`

## 本机固定位置

- Android 源码工程：`/Users/chaoliu/Documents/iosTest/guitarV4.5-Android`
- 正式发布目录：`/Users/chaoliu/Documents/iosTest/D15Guitar-Android-Release`
- 正式 APK：`D15Guitar-Android-v1.1.0.apk`
- 商店 AAB：`D15Guitar-Android-v1.1.0.aab`
- 下载中心 Git：`/Users/chaoliu/Documents/iosTest/d15-downloads`

正式对外发包只使用固定发布目录中的产物，不使用 `app/build/outputs/` 里的 Gradle 中间文件。

## 当前公开版本

- 版本：`1.1.0 (Build 4)`
- 发布日期：`2026-08-28`
- APK SHA-256：`abb4afcbc434e309e6e6ade0e98dcb3296a71d24b840e34ad18fdb5df2f71bd4`
- Android 源码提交：`79e54e1f6032bcde7db25b65ab295e98da3688f9`
- 更新记录：[`CHANGELOG.md`](CHANGELOG.md)
- 当前版本元数据：[`downloads/android/latest.json`](downloads/android/latest.json)

## 自己发布新版本

1. 修改 Android 工程中的 `versionCode`，每次正式发布必须加 1。
2. 在 Android 工程根目录执行 `./build_release.sh`。
3. 确认 APK/AAB 已生成到本机固定发布目录，且测试、Lint和签名校验通过。
4. 复制正式 APK，把副本改名为 `D15Guitar-Android-latest.apk`；原正式文件不要改名或删除。
5. 打开上面的“自己替换最新版”链接。
6. 删除页面上旧的同名 APK 附件。
7. 上传新的 `D15Guitar-Android-latest.apk`，等待上传成功标记出现。
8. 点击页面底部“更新”。不要修改 `android-latest` 标签，也不要另建版本标签。
9. 更新并提交 `ANDROID_RELEASE.md`、`CHANGELOG.md`、`downloads/android/README.md` 和 `downloads/android/latest.json`。
10. 从用户永久下载链接重新下载一次，运行 `shasum -a 256 下载到的APK路径`，确认结果与记录一致。

APK 只放在 Gitee Release，不再提交进普通 Git。Git 只保存版本号、更新内容、源码提交和 APK 校验值，避免每次发布让仓库增加约 20 MiB。

## 相关仓库与页面

- Gitee 下载中心：<https://gitee.com/d15cyber/d15-downloads>
- Gitee Android 发行版：<https://gitee.com/d15cyber/d15-downloads/releases/tag/android-latest>
- Android 源码仓库：<https://gitee.com/d15cyber/cyber-guitar-android>
- GitHub 下载中心镜像：<https://github.com/xiangaxiang/d15-downloads>

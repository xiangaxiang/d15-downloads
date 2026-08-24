# Android 当前正式安装包

此目录始终只保留一份当前最新版 APK，方便在 Git 仓库文件树中直接查看和下载。

## 当前版本

- 版本：`1.1.0 (Build 3)`
- 发布日期：`2026-08-24`
- 包名：`com.d15cyber.guitar`
- 文件：`D15Guitar-Android-latest.apk`
- 大小：`21,108,381 bytes`
- SHA-256：`2427a3480a16957c9fc70b1bb289bcd155fb7db3f0609592f2504890ff186a2b`
- Android 源码提交：`74ebccd998dfdb6beac898279a3d7c21492a1204`
- 完整更新内容：[`CHANGELOG.md`](../../CHANGELOG.md)
- 固定公开下载地址：[D15Guitar-Android-latest.apk](https://gitee.com/d15cyber/d15-downloads/releases/download/android-latest/D15Guitar-Android-latest.apk)

## 后续发布规则

每次 Android 正式发布必须同时完成以下事项：

1. 使用 Android 工程根目录的 `build_release.sh` 生成并验证正式签名 APK/AAB。
2. 将正式 APK 覆盖到本目录的 `D15Guitar-Android-latest.apk`，目录中不堆放多个版本文件。
3. 更新本文件、根目录 `README.md`、`CHANGELOG.md` 和 `latest.json` 中的版本、日期、源码提交、文件大小及 SHA-256。
4. 将以上文件与 APK 一起提交并推送到下载中心 Git 仓库。
5. 替换 Gitee `android-latest` 发行版中的同名附件，保持外部下载链接和二维码不变。
6. 从公开下载链接重新下载 APK，并确认 SHA-256 与 Git 目录中的 APK 完全一致。

即使只在目录中保留一个同名 APK，普通 Git 历史仍会保存每次提交的二进制对象，所以仓库体积会随正式发布次数增长。若后续体积明显过大，再评估 Git LFS 或独立制品存储；不得通过重写公开 Git 历史来偷偷删除旧版本。

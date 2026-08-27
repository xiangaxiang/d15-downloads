# Android 正式发布记录与操作说明

APK 只保存在 Gitee `android-latest` 发行版，不提交进普通 Git。此目录保存当前版本元数据和人工发布步骤；
每次更新都必须提交记录，避免只替换安装包而无法追溯。

## 当前版本

- 版本：`1.1.0 (Build 4)`
- 发布日期：`2026-08-28`
- 包名：`com.d15cyber.guitar`
- Release 附件：`D15Guitar-Android-latest.apk`
- 大小：`21,108,381 bytes`
- SHA-256：`abb4afcbc434e309e6e6ade0e98dcb3296a71d24b840e34ad18fdb5df2f71bd4`
- Android 源码提交：`79e54e1f6032bcde7db25b65ab295e98da3688f9`
- 完整更新内容：[`CHANGELOG.md`](../../CHANGELOG.md)
- 固定公开下载地址：[D15Guitar-Android-latest.apk](https://gitee.com/d15cyber/d15-downloads/releases/download/android-latest/D15Guitar-Android-latest.apk)

## 后续发布规则

每次 Android 正式发布必须同时完成以下事项：

1. 使用 Android 工程根目录的 `build_release.sh` 生成并验证正式签名 APK/AAB。
2. 本机正式产物固定在 `/Users/chaoliu/Documents/iosTest/D15Guitar-Android-Release/`。APK 文件名为
   `D15Guitar-Android-v<versionName>.apk`，AAB 同理；不要从 Gradle 中间目录对外发包。
3. 更新本文件、根目录 `CHANGELOG.md` 和 `latest.json` 中的版本、日期、源码提交、文件大小及 SHA-256；
   根目录 `README.md` 只保留稳定下载入口，不在首页堆版本记录。
4. 提交并推送这些文本记录；`downloads/android/*.apk` 已被 `.gitignore` 排除，不要强制加入 Git。
5. 替换 Gitee `android-latest` 发行版中的同名附件，保持外部下载链接和二维码不变。
6. 从公开下载链接重新下载 APK，并确认 SHA-256 与本机正式 APK 完全一致。

## 自己通过网页发布 APK

1. 打开本机固定目录，复制 `D15Guitar-Android-v1.1.0.apk`，把副本改名为
   `D15Guitar-Android-latest.apk`；原正式文件不要改名或删除。
2. 登录 Gitee，打开：
   `https://gitee.com/d15cyber/d15-downloads/releases/android-latest/edit`
3. 在“已存在附件”中删除旧的 `D15Guitar-Android-latest.apk`。
4. 将刚才改名的副本拖到上传区域，等待文件旁出现上传成功标记。
5. 点击页面底部“更新”。不要改标签 `android-latest`，不要另建版本标签，否则永久下载链接和二维码会变化。
6. 打开固定下载地址实际下载一次，并用 macOS 终端执行
   `shasum -a 256 下载到的APK路径`，结果必须与 `latest.json` 一致。

Gitee Release 附件由网页单独保存，不属于 Git 文件树。替换附件不会让 Git 仓库每次增加约 20 MiB；
版本追溯依靠 `CHANGELOG.md`、`latest.json`、Android 源码提交和 APK SHA-256。

# D15 Guitar Android 发布记录

本文件记录所有正式对外发布的 Android 版本。APK 保存在 Gitee `android-latest` 发行版，不提交进普通 Git；
Git 永久保留每版的版本号、发布时间、源码提交、SHA-256、更新内容和验证结果。

## 1.1.0 (Build 4) — 2026-08-28

### 安装包

- Gitee Release 附件：`D15Guitar-Android-latest.apk`
- 包名：`com.d15cyber.guitar`
- Android 源码提交：`79e54e1f6032bcde7db25b65ab295e98da3688f9`
- SHA-256：`abb4afcbc434e309e6e6ade0e98dcb3296a71d24b840e34ad18fdb5df2f71bd4`
- 大小：`21,108,381 bytes`

### 本版更新

- 修复 Android 15 / 小米 HyperOS 上蓝牙连接弹层可能顶入状态栏或显示挖孔，导致顶部控件无法点击的问题。
- 去掉使用 `Configuration.screenHeightDp` 计算弹层高度的逻辑，改用 `WindowInsets.safeDrawing` 约束安全区域。
- 蓝牙扫描、连接、BLE MIDI、USB MIDI、歌曲、伴奏和音频逻辑没有修改。
- 弹层保留关闭键、系统返回键和点击遮罩关闭；本版自定义安全区弹层不提供下滑关闭。

### 构建与验证

- 80 个正式单元测试通过，0 failure、0 error。
- Android Lint：0 error；38 warning、4 information。
- 四种 ABI、正式 APK/AAB 和签名校验通过。
- 已覆盖安装到 Redmi 测试机，用户确认蓝牙页标题、关闭、扫描、设备选择、滚动及安全区正常。
- 发生原问题的小米 15 尚待客户使用 Build 4 复测。

## 1.1.0 (Build 3) — 2026-08-24

### 安装包

- Gitee Release 附件：`D15Guitar-Android-latest.apk`
- 包名：`com.d15cyber.guitar`
- Android 源码提交：`74ebccd998dfdb6beac898279a3d7c21492a1204`
- SHA-256：`2427a3480a16957c9fc70b1bb289bcd155fb7db3f0609592f2504890ff186a2b`
- 大小：`21,108,381 bytes`

### 本版主要更新

- 智能谱支持从单个 JSON、目录、ZIP 和用户确认后的公开 HTTPS URL 导入。
- URL/ZIP 导入增加下载大小、文件数量、解压容量、路径穿越和文件类型等安全限制。
- 优化批量歌曲导入速度；空 `melody.name` 使用结构字段回退，不再导致大批歌曲直接失败。
- 追平智能谱多轨伴奏：主旋律、鼓机、节拍器以及独立吉他轨道的开关和音量。
- 自动播放与跟弹统一 transport，补齐 3/4、4/4、6/8、section 边界和跨段音符生命周期。
- 修正跟弹键位颜色、扫弦切换、半自动模式、歌词 section 排布和长时间演奏累计延迟等问题。
- 每首智能谱独立保存 CAPO、BPM、演奏方式和节奏型，与自由弹唱设置互不影响。
- 所选 SoundFont 同时供全部演奏轨道使用；缺少音色时明确提示，不再静默更换备用音源。
- 补充有线 Type-C、耳机和其他音频路由切换后的恢复逻辑。
- 统一并收紧 Android UI 字体、间距、圆角、弹层和控件视觉尺寸。
- 内置两首公共领域多轨示例；外部 200 首曲谱包不打入 App。

### 构建验证

- 80 个正式单元测试通过，0 failure、0 error。
- Android Lint：0 error；38 warning、4 information。
- 四种 ABI native 产物、正式 APK 和 AAB 构建成功。
- APK v2 签名与 AAB 签名验证通过。
- 已覆盖安装到测试手机，保留原有歌曲和设置。

### 仍需关注

- BLE MIDI、USB MIDI、蓝牙音箱、Type-C/USB Audio、3.5mm 耳机及后台恢复仍需持续真机回归。
- 首次连接时手机与吉他两侧参数冲突的同步规则尚未统一。
- 新格式 200 首中仍有 12 首因两端不支持的非规范和弦符号而被明确拒绝。

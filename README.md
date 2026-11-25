# mos-releases

mos 安卓应用的在线升级发布仓库（公开）。

- `update.json`：mos 应用启动时读取，判断是否有新版本。
- APK 以 GitHub Release 附件发布，`update.json` 里的 `downloads.android` 指向对应 Release 的 APK。

发布流程：Codemagic 构建成功后，把 APK 作为 Release 附件上传，并更新 `update.json`（version / build / releasedAt / notes / downloads.android）。

签名：所有 APK 用同一把 mos 发布 keystore 签名（keystore 文件与密码另存，不在仓库里），保证覆盖升级。

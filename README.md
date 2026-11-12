# XiaoYuScan

「小羽扫描」应用内更新用的版本清单仓库（包名 `cc.fornow.scan`）。

## 文件

- `version.json` — 应用的版本清单。App 的「我的 → 检查更新」会依次请求以下三条线路，任一成功即生效，全部失败则提示已是最新版本：
  1. `https://cdn.jsdelivr.net/gh/fornow330/XiaoYuScan@main/version.json`（国内 CDN）
  2. `https://raw.githubusercontent.com/fornow330/XiaoYuScan/main/version.json`（GitHub 直连）
  3. `https://ghproxy.net/https://raw.githubusercontent.com/fornow330/XiaoYuScan/main/version.json`（镜像）

## 字段

```json
{
  "versionCode": 2,
  "versionName": "1.1.0",
  "notes": "更新内容",
  "downloadUrl": "https://my.feishu.cn/drive/folder/NRP0fyYGwljMmPdBZNmcYl9Vnuh"
}
```

`versionCode` 必须大于 App 当前 `BuildConfig.VERSION_CODE` 才会提示更新。

## 发版流程

1. 改 `app/build.gradle` 的 `versionCode` +1、`versionName` 升位；
2. `gradle assembleDebug` 出包，连同说明打包成 `小羽扫描_v<版本>.zip`；
3. 上传到飞书云盘「小羽扫描」文件夹，只保留最新三个版本；
4. 更新本仓库 `version.json` 的 `versionCode` / `versionName` / `notes`。

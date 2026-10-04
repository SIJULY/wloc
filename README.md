# Apple WLOC 定位修改

修改 Apple 网络定位服务 (WiFi/基站) 返回的坐标，实现 iOS 网络定位虚拟定位。

## 模块一：WLOC 定位修改（Shadowrocket，默认伦敦）

```
https://raw.githubusercontent.com/SIJULY/wloc/refs/heads/main/modules/wloc.module
```

- `modules/wloc.module` — Shadowrocket 模块（默认坐标：英国伦敦，可修改 argument 换城市）
- `dist/wloc.js` — 拦截 `/clls/wloc` 响应并替换坐标
- `dist/wloc-settings.js` — 拦截选点设置请求并持久化坐标

## 模块二：iOS Location Spoofer（无状态版，Shadowrocket / Surge / Egern，默认伦敦）

```
https://raw.githubusercontent.com/SIJULY/wloc/refs/heads/main/ios-location-spoofer/ios-location-spoofer.sgmodule
```

无状态版：坐标写入每台设备各自的本机存储，可公开共用、多人互不覆盖。
**本仓库版本已在 argument 里写死伦敦坐标**（`enabled=true&latitude=51.5074&longitude=-0.1278&altitude=25`），
装上即用；模块 argument 优先级高于本机存储，如需换城市直接改 argument 里的经纬度即可。
想改其他参数（海拔、精度等）同样在 argument 那一行加，如 `&horizontalAccuracy=15`。

- `ios-location-spoofer/ios-location-spoofer.sgmodule` — 模块文件
- `ios-location-spoofer/location-spoofer.js` — 拦截响应并替换坐标
- `ios-location-spoofer/location-settings.js` — 拦截选点储存请求

## 分流规则集

- `ruleset/muse.yaml` — Muse (Meta AI) 域名规则 (classical 格式)，目前收录 `muse.ai`、`metaaivm.com`、`meta.ai`。
  在 OpenClash/Clash 中引用：

  ```yaml
  rule-providers:
    muse:
      type: http
      behavior: classical
      url: https://raw.githubusercontent.com/SIJULY/wloc/refs/heads/main/ruleset/muse.yaml
      path: ./ruleset/muse.yaml
      interval: 86400
  ```

  ```yaml
  rules:
    - RULE-SET,muse,🇺🇸 美国节点
  ```

  注意：Muse 目前仅美加开放，建议走美国节点；`meta.com` 有意未收录（范围太广）。

## 上游来源

- WLOC 模块原仓库 [Yu9191/wloc](https://github.com/Yu9191/wloc) 已删除，脚本来自 fork：[reihard/yu9191-wloc](https://github.com/reihard/yu9191-wloc)
- iOS Location Spoofer 来自：[cyberhandyman/ios-location-spoofer](https://github.com/cyberhandyman/ios-location-spoofer)

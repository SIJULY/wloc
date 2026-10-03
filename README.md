# Apple WLOC 定位修改

修改 Apple 网络定位服务 (WiFi/基站) 返回的坐标，实现 iOS 网络定位虚拟定位。

## 模块一：WLOC 定位修改（Shadowrocket，默认伦敦）

```
https://raw.githubusercontent.com/SIJULY/wloc/refs/heads/main/modules/wloc.module
```

- `modules/wloc.module` — Shadowrocket 模块（默认坐标：英国伦敦，可修改 argument 换城市）
- `dist/wloc.js` — 拦截 `/clls/wloc` 响应并替换坐标
- `dist/wloc-settings.js` — 拦截选点设置请求并持久化坐标

## 模块二：iOS Location Spoofer（无状态版，Shadowrocket / Surge / Egern）

```
https://raw.githubusercontent.com/SIJULY/wloc/refs/heads/main/ios-location-spoofer/ios-location-spoofer.sgmodule
```

无状态版：坐标写入每台设备各自的本机存储，可公开共用、多人互不覆盖。
**注意**：此版本坐标不写在模块里，需搭配选点页使用（在地图上选位置 → 储存到设备），
未选点时默认透传真实定位。想定到伦敦的话，在选点页里选伦敦即可。

- `ios-location-spoofer/ios-location-spoofer.sgmodule` — 模块文件
- `ios-location-spoofer/location-spoofer.js` — 拦截响应并替换坐标
- `ios-location-spoofer/location-settings.js` — 拦截选点储存请求

## 上游来源

- WLOC 模块原仓库 [Yu9191/wloc](https://github.com/Yu9191/wloc) 已删除，脚本来自 fork：[reihard/yu9191-wloc](https://github.com/reihard/yu9191-wloc)
- iOS Location Spoofer 来自：[cyberhandyman/ios-location-spoofer](https://github.com/cyberhandyman/ios-location-spoofer)

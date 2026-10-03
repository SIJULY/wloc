# Apple WLOC 定位修改

修改 Apple 网络定位服务 (WiFi/基站) 返回的坐标，实现 iOS 网络定位虚拟定位。

## Shadowrocket 模块订阅

```
https://raw.githubusercontent.com/SIJULY/wloc/refs/heads/main/modules/wloc.module
```

## 文件说明

- `modules/wloc.module` — Shadowrocket 模块（默认坐标：英国伦敦，可修改 argument 换城市）
- `dist/wloc.js` — 拦截 `/clls/wloc` 响应并替换坐标
- `dist/wloc-settings.js` — 拦截选点设置请求并持久化坐标

## 上游来源

原仓库 [Yu9191/wloc](https://github.com/Yu9191/wloc) 已删除，脚本来自 fork：[reihard/yu9191-wloc](https://github.com/reihard/yu9191-wloc)。

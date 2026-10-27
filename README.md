# fph-fpk · 屋事小记 飞牛 fnOS 应用分发仓

屋事小记（family-parcel-hub）的 **fpk 纯分发仓**：只放发布产物与商店索引，不含源码。

## 用途

- **Moo 应用商店**：「应用源 → 添加」贴本仓库链接即可浏览 / 安装 / 更新：
  ```
  https://github.com/zsunny6658/fph-fpk
  ```
- **手动安装**：到 [Releases](https://github.com/zsunny6658/fph-fpk/releases) 下载 `fph_x.y.z.fpk`，
  飞牛「应用中心 → 手动安装」选择该文件
- 后续可扩展 FnDepot 索引（`fnpack.json`）等其他第三方商店格式

## 与其他仓库的关系

| 仓库 | 职责 |
|------|------|
| [`family-parcel-hub-api`](https://github.com/zsunny6658/family-parcel-hub-api) | 开发主仓：服务端 + 内置 H5 + fpk 打包模板（`scripts/build-fpk.sh` 构建） |
| [`wushixiaoji-miniprogram`](https://github.com/zsunny6658/wushixiaoji-miniprogram) | 微信小程序客户端 |
| **本仓 `fph-fpk`** | fpk 分发：Release 产物 + `moo.json` 商店索引 |

发版流程：主仓打 tag / 发版时构建 fpk → 上传本仓 Release → 更新本仓 `moo.json`（版本号 / sha256 / 下载直链）。

## 安装说明

- 桌面图标点击即开 H5（独立端口 5189 直连，不走网关反代）
- 数据目录 `/var/apps/fph/var/data`，升级/卸载均保留
- 服务端要求 Node ≥ 22.5（fnOS 自带 Node 版本不足时启动脚本会明确报错）

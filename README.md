# iHealth

> 使用佳明（Garmin）手表采集心率数据，并将数据同步展示到 GitHub 主页 —— Your Soul, Your Beats!

本项目 fork 自 [yihong0618/iBeats](https://github.com/yihong0618/iBeats)。它会把你手表采集到的心率数据渲染成一张动态心形 SVG 和一份心率表格，自动更新到你的个人主页 README 上。

![](./files/heart.svg)

<!--START_SECTION:my_heart_rate-->
| Time | Rate | 
 | ---- | ---- | 
| 2026年1月1日 19:50 | 98 |
| 2026年1月1日 19:48 | 99 |
| 2026年1月1日 19:46 | 95 |
| 2026年1月1日 19:44 | 94 |
| 2026年1月1日 19:42 | 94 |

<!--END_SECTION:my_heart_rate-->

## ✨ 原理

1. 通过 iOS `快捷指令（Shortcuts）` 读取健康数据中的心率（时间 + 数值）。
2. `快捷指令` 携带数据触发本仓库的 GitHub Actions（`workflow_dispatch`）。
3. Actions 运行 `main.py`，将数据写入 README 的占位区域，并生成心形 SVG（`files/heart.svg`）。
4. 自动 commit & push，主页心率随之刷新。

# 步骤
1. 参考[iBeats](https://github.com/yihong0618/iBeats)

# GitHub Actions

1. fork or clone this repo
2. change the secrets (GitHub token)
3. config iOS `Shortcuts` 
4. trigger by iOS `Shortcuts`

# 特别感谢
- @[yihong0618](https://github.com/yihong0618)
- @[wuhan005](https://github.com/wuhan005) 特别棒的项目 [mebeats](https://github.com/wuhan005/mebeats)
- @[L1cardo](https://github.com/L1cardo) idea

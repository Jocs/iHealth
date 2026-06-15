# iHealth

> 使用佳明（Garmin）手表采集心率数据，并将数据同步展示到 GitHub 主页 —— Your Soul, Your Beats!

本项目 fork 自 [yihong0618/iBeats](https://github.com/yihong0618/iBeats)。它会把你手表采集到的心率数据渲染成一张动态心形 SVG 和一份心率表格，自动更新到你的个人主页 README 上。

![](./files/heart.svg)

<!--START_SECTION:my_heart_rate-->

<!--END_SECTION:my_heart_rate-->

## ✨ 原理

1. 通过 iOS `快捷指令（Shortcuts）` 读取健康数据中的心率（时间 + 数值）。
2. `快捷指令` 携带数据触发本仓库的 GitHub Actions（`workflow_dispatch`）。
3. Actions 运行 `main.py`，将数据写入 README 的占位区域，并生成心形 SVG（`files/heart.svg`）。
4. 自动 commit & push，主页心率随之刷新。

## 🚀 使用步骤

### 1. Fork 本仓库

点击右上角 `Fork`，将仓库复制到你自己的账号下。

### 2. 修改工作流配置

编辑 `.github/workflows/replace_readme.yml`，把以下两个环境变量改成你自己的信息（用于自动提交）：

```yaml
env:
  GITHUB_NAME: your_name
  GITHUB_EMAIL: your_email@example.com
```

> 默认使用仓库自带的 `GITHUB_TOKEN` 即可向自己的仓库推送，无需额外配置。

### 3. 配置 iOS 快捷指令

参考上游项目 [iBeats](https://github.com/yihong0618/iBeats) 创建快捷指令，主要完成：

- 从「健康」App 读取心率的**时间列表**与**数值列表**；
- 调用 GitHub API 触发本仓库的 `workflow_dispatch`，并把两个列表分别作为 `time` 和 `value` 入参传入。

### 4. 触发同步

运行快捷指令即可触发 GitHub Actions，稍等片刻主页 README 与心形图便会自动更新。
也可以在仓库的 `Actions` 页面手动运行 `Replace README AND GENERATE SVG` 工作流进行测试。

## 🛠 本地运行

```bash
pip install -r requirements.txt
python main.py "$TIME_LIST" "$VALUE_LIST"
```

其中 `$TIME_LIST` 与 `$VALUE_LIST` 为按行分隔的时间与心率数值。

# 特别感谢
- @[yihong0618](https://github.com/yihong0618)
- @[wuhan005](https://github.com/wuhan005) 特别棒的项目 [mebeats](https://github.com/wuhan005/mebeats)
- @[L1cardo](https://github.com/L1cardo) idea

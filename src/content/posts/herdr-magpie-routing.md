---
title: 把 Magpie Routing 带进 Herdr：从路由图到 Context Window
published: 2026-11-13
description: 给 Herdr 做了一个 Magpie Routing 布局：实时看 Agent 到模型的路由，也能按会话查看 Context Window。
tags:
  - Herdr
  - Magpie
  - 工具实践
  - Agent
lang: zh
abbrlink: herdr-magpie-routing
toc: true
---

Herdr 的布局和面板可以由本地 mod 组合。我想把 Magpie 已有的 Routing 界面带进 Herdr：在 Files、Changes 旁加一个 Routing 开关，打开后能看请求从 Agent 走向哪个模型；下方再选一个会话，查看它的 Context Window。

![Herdr 中的 Magpie Routing 布局](https://raw.githubusercontent.com/sanshansss/herdr-routing-layout/main/layouts/layout.png)

![按会话查看 Context Window](https://raw.githubusercontent.com/sanshansss/herdr-routing-layout/main/layouts/contextwindow.png)

截图中的空间名、会话标识、路径和终端内容都已做马赛克。

## 从一张路由图开始

这个想法来自 [lexrus 的推文和评论](https://x.com/lexrus/status/2119443089760960679)。我参考的提示词大意是：读 Herdr 的 `AGENTS.md` 和 Magpie 本地源码，复刻 Routing 动画，再做一个实时展示路由的 Herdr mod，并在 Files、Changes 旁加开关。

最初只想复刻上方的路由图。后来把 Magpie 下方的 Context Window 也加进来，并做成按会话选择：切换会话时，下面显示该会话最近一次可用的上下文统计。

## 让真实路由数据驱动画面

面板读取 Magpie 写入本机 `~/.config/magpie/routing/*.jsonl` 的记录，通过目录监听响应更新，并以 25 秒间隔兜底刷新。它展示路由记录里的 token、窗口容量、上下文 parts 和条目分类；不会显示原始对话正文。

动画也有一个实际限制：Herdr 的 mod 使用 GPUI 原生组件，没有沿任意贝塞尔曲线做关键帧动画的接口。连线保留贝塞尔曲线，飞行圆点则用原生 transition 在路径端点间移动。视觉方向和 Magpie 接近，但不是逐帧完全相同。

## 获取和安装

布局包在 [GitHub 仓库](https://github.com/sanshansss/herdr-routing-layout)，包含布局文件、Routing 面板、顶部开关和基于 Skillshare 的面板。已经在 Herdr app 0.1.14 上验证。Routing 数据需要 Magpie 在本机写入日志；Skillshare 面板的功能还需要 `skillshare` CLI。

想让本机 Agent 安装，可以把这段提示词交给它：

```text
读 ~/.config/herdr-app/AGENTS.md，然后从 https://github.com/sanshansss/herdr-routing-layout 获取 magpie-routing-v1/，按其中 RECIPE.md 安装布局和所需 mods。先检查并备份同名文件，不要改动其他配置；安装后运行 herdr-app check 和 herdr-app status，确认无错误后切换到这个布局。
```

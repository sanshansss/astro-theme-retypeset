---
title: 空间飞行器动力学教学动画
published: 2026-10-20
description: 9 支面向空间飞行器姿态动力学、轨道力学与姿态执行机构的中文教学动画。
tags:
  - 空间飞行器
  - 动力学
  - 教学动画
pin: 99
lang: zh
abbrlink: spacecraft-dynamics-animations
toc: false
---

我完成了一组空间飞行器动力学教学动画，共 9 支，使用 Python 自写动力学模型与
Manim 制作。动画采用中文标注，内容覆盖姿态运动学、刚体自旋稳定性、能量耗散、
引力梯度、太阳同步轨道、CW 相对运动、引力弹弓以及反作用轮和 CMG。

主要作品包括：

- 3-1-2 欧拉角转序与转序不可交换；
- Explorer 1 在能量耗散下的最小惯量轴自旋失稳；
- 最大惯量轴与中间惯量轴自旋稳定性对比；
- 引力梯度稳定的天平动与不稳定构型发散过程；
- 太阳同步轨道的节点进动、倾角—高度关系和一年尺度地方时保持；
- CW 自然闭合绕飞与 V-bar 双脉冲交会；
- 引力弹弓在行星系和日心系中的速度变化；
- 反作用轮角动量交换、饱和卸载和 CMG 奇异几何。

全部成片与核心代码已整理到 GitHub：

::github{repo="sanshansss/spacecraft-dynamics-animations"}

- 项目仓库：<https://github.com/sanshansss/spacecraft-dynamics-animations>
- 个人主页：<https://sanshansss.github.io/astro-theme-retypeset/>

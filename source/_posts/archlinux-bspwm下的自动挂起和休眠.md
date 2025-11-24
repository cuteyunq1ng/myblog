---
title: archlinux+bspwm下的自动挂起和休眠
categories: linux
keywords: "休眠"
abbrlink: bb371655
date: 2025-11-24 20:45:33
updated: 2025-11-24 20:45:33
top_img:
cover:
tags:
  - tile
  - suspend
  - hibernate
description: "  解决 `linux` 轻量安装下的自动锁屏、挂起和休眠问题, 主要工具：`xidlehook`, 锁屏工具: `betterlockscreen`
" 
series:
---

## 主旨

解决 `linux` 轻量安装下的自动锁屏、挂起和休眠问题, 主要工具：`xidlehook`, 锁屏工具: `betterlockscreen`

## xidlehook

`xidlehook` 是一个用 `Rust` 编写的工具，它是 `xautolock` 的现代化替代品。它的杀手级功能是 检测音频 —— 如果在看视频或听音乐，它不会自动挂起。

1. 安装

``` bash
    yay -S xidlehook betterlockscreen
```

2. 在 `bspwm` 启动脚本中配置

``` bash
    # 启动 xidlehook
    # --not-when-audio : 播放音频时不计时
    # --not-when-fullscreen : 全屏时不计时 (玩游戏/看电影)
    # --timer <秒> <动作> <恢复动作>
    xidlehook \
    --not-when-audio \
    --not-when-fullscreen \
    --timer 30 \
        'light -U 40' \
        'light -A 40' \
    --timer 180 \
        'betterlockscreen -l dim' \
        '' \
    --timer 300 \
        'systemctl suspend' \
        '' \
    --timer 600 \
        'systemctl hibernate' \
        '' &
```

## 确保合盖和手动挂起时锁屏 (xss-lock)

如果你直接合上笔记本盖子，或者手动输入 `systemctl suspend`，系统会挂起，但唤醒时可能不会锁屏。为了解决这个问题，我们需要 `xss-lock`。它监听 systemd 的信号，一旦发现系统要休眠了，就强制先锁屏。

``` bash
    yay -S xss-lock
    # 指定当你合盖或系统休眠时，使用什么命令来锁屏
    # 这里以 betterlockscreen 为例
    # 将下行命令添加到 bspwm 启动脚本中
    xss-lock --transfer-sleep-lock -- betterlockscreen -l dim &
```

## tlp

`TLP` 是 `Linux` 系统下最流行、功能最强大的高级电源管理工具，主要用于优化笔记本电脑的电池续航。
它的核心理念是 “安装即忘” (Install and Forget)。安装后，它会自动在后台运行，根据你当前是“接通电源 (AC)”还是“使用电池 (Battery)”的状态，自动调整系统的硬件参数以达到最佳的性能或最省电的效果。

1. 安装工具

``` bash
    # 安装 tlp
    sudo pacman -S tlp

     # (可选) 如果你是 ThinkPad 用户，建议安装此包以获得更精确的电量读取
    sudo pacman -S tp_smapi acpi_call
```

2. 启动服务

``` bash
    sudo systemctl enable tlp.service
    sudo systemctl start tlp.service
```

3. 检查状态

``` bash
    # 查看简要状态
    sudo tlp-stat -s
    # 查看电池详细信息（包括损耗程度）
    sudo tlp-stat -b
```

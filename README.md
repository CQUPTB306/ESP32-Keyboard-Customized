# ESP32-Keyboard-Customized
一个多功能的5键键盘，基于ESP32-C3。

![IMG_20250328_122641](https://github.com/user-attachments/assets/e44e63d6-a83e-4bbb-9b9e-1eea8c9908c4)

## 功能

- [√]发送单个按键
- [√]发送组合键
- [-]发送媒体键
- [√]倒计时定时器
- [√]节拍器
- [√]加载其他预设
- [-]不修改代码创建新预设
- [√]电池电压监测和管理
- [-]自动重连

现在有 5 个预设可用（Ctrl X/C/V; VSCode 快捷键; 常用的系统快捷键; EDA...）你可以在代码中修改它们以满足需要。

## 硬件

本项目使用 ESP32-C3-mini-1 模块，配备 5 个机械按键轴、1 个无源蜂鸣器和 1 个指示灯。

使用 0.91 英寸 OLED 显示屏（128x32）作为界面显示。

使用 TP4056 模块和 3.7V 锂电池供电。

具体引脚设置如下：

```
// 引脚定义
#define ADC_PIN         A0
#define BUZZER_PIN      1
#define BTN_1_PIN       2
#define BTN_2_PIN       3
#define BTN_3_PIN       4
#define BTN_4_PIN       5
#define OLED_SDA        6
#define OLED_SCL        7
#define BTN_5_PIN       8
#define STATUS_LED      10
```


*按键应设置为上拉模式。如果没有外部上拉电阻，请将每个按键的 pinMode 更改为`INPUT_PULLUP`（在 KEY_Init()函数中）。*


## 使用方法

请使用 PlatformIO 导入项目文件夹/下载程序。
默认按键设置应为：

`BTN_1_PIN`：Ctrl+X

`BTN_2_PIN`：Ctrl+C

`BTN_3_PIN`：Ctrl+V

`BTN_4_PIN`：无

`BTN_5_PIN`：无


• 按住`BTN_4_PIN`进入节拍器模式

• 按住`BTN_5_PIN`进入定时器设置界面

• 同时按住 KEY4 和 KEY5 修改按键映射（预设）

进入这些模式后，要返回请按住 KEY5`BTN_5_PIN`

---

*代码不够健壮，存在漏洞。如果您能提出修改建议或提供代码，将不胜感激。*

*已知问题：*

- *从主模式返回时会异常触发额外的按键操作*
- ~~*启用节拍器后返回主模式，按键操作无效*~~ （已修复）
- *按键逻辑有点差:(*

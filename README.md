
# README（精简工程实用风格，可直接使用）
本工程可将 Bluepill（STM32F103C8T6）固件编译为 CMSIS-DAP（DapLink）调试器，还支持CDC串口。

原版仓库直接编译会出现依赖缺失报错，本仓库重新整理并补齐全部相关依赖。

## 编译开启宏定义
```
USE_STDPERIPH_DRIVER,STM32F10X_MD,BLUEPILL,SWD_REMAP,SWO_PB7,USBD_CDC_ACM_ENABLE=1
```

## 烧录
可以直接用这个固件：`F103-DAP-SWO-CDC-BLUEPILL-SWD_REMAP.hex`

## 引脚接线
DAP调试器(Bluepill) ↔ 目标设备
```
SWCLK(PA14)      SWCLK(PA14)
SWDIO(PA13)      SWDIO(PA13)
SWO(PB7)         SWO(PB3)

CDC串口虚拟通道：
TX(PA9)          RX(PA10)
RX(PA10)         TX(PA9)
```

## 说明
SWO ITM日志通道本人暂未调试成功；
该方式属于不占用硬件串口的内核日志输出方案，可供后续研究参考：
https://zhuanlan.zhihu.com/p/676727734

---

# 原文
# STM32F103C8T6_CMSIS-DAP_SWO
-----------------------------
Based x893's code on: https://github.com/x893/CMSIS-DAP

My contribution:

1. Upgrade CMSIS-DAP version to V2.0.0 (HID mode, not WinUSB) .
2. Enable SWO_UART function(USART1), no SWO_STREAM/SWO_MANCHESTER mode.
3. CDC function improved(USART2).
4. Added a Soft-Reset function for Cortex-M.
5. Added BluePill board support, Remapped or unRemap (refer to Docs).
6. Added STLINK_V2A, STLINK_V2B board support (refer to Docs).
7. Minor changes, e.g. LED handling, project files re-group......
 -

Here is the BluePill remapped SWD port in use:
![alt text](https://github.com/RadioOperator/STM32F103C8T6_CMSIS-DAP_SWO/blob/master/Doc/Bluepill/1.SWD_Remapped.jpg) 
 -
 -
 -
Check my another repository for USB2.0 High-Speed CMSIS-DAP device, incredible more:
 -
 - https://github.com/RadioOperator/CMSIS-DAP_for_STLINK-V3MINI
 -
 - 




# Tuya IoTOS Embeded Demo WiFi & BLE Alcohol-Sensor

[English](./README.md) | [中文](./README_zh.md) 

## Introduction 

This Demo implements a smart alcohol detector through the Tuya Smart Cloud Platform, Tuya Smart APP, IoTOS Embeded WiFi &Ble SDK, using the Tuya WiFi/WiFi+BLE series modules to achieve remote data monitoring.

Implemented functions include.

+ Real-time detection of alcohol value in the current environment




## Quick start 

### Compile & Burn
+ Download [Tuya IoTOS Embeded WiFi & BLE sdk](https://github.com/tuya/tuya-iotos-embeded-sdk-wifi-ble-bk7231t) 

+ Download the demo to the apps directory of the SDK directory 

  ```bash
  $ cd apps
  $ git clone https://registry.code.tuya-inc.top/hardware_developer/tuya-iotos-embeded-demo-ble-alcohol-sensor.git
  ```
  
+ Execute the following command in the SDK root directory to start compiling.

  ```bash
  sh build_app.sh apps/bk7231t_alcohol_sensor bk7231t_alcohol_sensor 1.0.0 
  ```

+ Firmware burning license information please refer to: [Wi-Fi + BLE series module burning license](https://developer.tuya.com/cn/docs/iot/device-development/burn-and-authorization/burn-and-authorize-wifi-ble-modules/burn-and-authorize-wb-series-modules?id=Ka78f4pttsytd) 

 

### Demo information 

|      Product ID      |                       vsfkspazqbkdvi5x                       |
| :------------------: | :----------------------------------------------------------: |
|    Chip Platform     |                           BK7231T                            |
| Compiler Environment | ty_iot_wf_bt_sdk_bk_bk7231t_1.0.2 (Tuya IOT Platform SDK 1.0.2) |

 

### File introduction 

```bash
├── include
│ ├── app_adc.h
│ ├── soc
│ │ ├── soc_adc.h
│ ├── tuya_alcohol_sensor.h
│ ├── tuya_device.h
│ └── tuya_dp_process.h
└── src
    ├─ app_adc.c
    ├── soc
    │ └── soc_adc.c
    ├── tuya_alcohol_sensor.c
    ├── tuya_device.c
    └── tuya_dp_process.c
```



### Demo entry

Entry file: tuya_device.c

Important functions: device_init()

+ Call tuya_iot_wf_soc_dev_init_param() interface to initialize the SDK, configure the operating mode, the mating mode, and register various callback functions and store the firmware key and PID.

+ Calling the tuya_iot_reg_get_wf_nw_stat_cb() interface to register the device network status callback functions.

+ Call the application layer initialization function air_box_device_init()



### DP point related

+ Report dp point interface: dev_report_dp_json_async()

| function name | OPERATE_RET dev_report_dp_json_async(IN CONST CHAR_T *dev_id,IN CONST TY_OBJ_DP_S *dp_data,IN CONST UINT_T cnt) |
| ------------- | ------------------------------------------------------------ |
| devid         | device id (if gateway, MCU, SOC class device then devid = NULL; if sub-device, then devid = sub-device_id) |
| dp_data       | dp structure array name                                      |
| cnt           | Number of elements of the dp structure array                 |
| return        | OPRT_OK: Success Other: Failure                              |



### I/O List 

| Flame sensor pins | Corresponding connected wb3s pins |
| :---------------: | :-------------------------------: |
|        VCC        |               3.3V                |
|        GND        |                GND                |
|        AO         |           ADC/GPIOA_23            |



## Related Documents

Tuya Demo Center: https://developer.tuya.com/en/demo/



## Technical Support

You can get support for Tuya by using the following methods:

- Developer Center: https://developer.tuya.com
- Help Center: https://support.tuya.com/en/help
- Technical Support Work Order Center: https://service.console.tuya.com

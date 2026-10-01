---
title: "DynamixelAXControl.cpp"
linkTitle: "DynamixelAXControl.cpp"
summary: "Implementación de la clase DynamixelAXControl (control de motores Dynamixel AX)."
description: "Implementación de la clase DynamixelAXControl (control de motores Dynamixel AX)."
weight: 20
---

Implementación de la clase [DynamixelAXControl](Classes/classDynamixelAXControl.md) (control de motores Dynamixel AX). [More...](#detailed-description)

## Defines

| Name |
| ---- |
| **[ADDR_MODEL_NUMBER](Files/DynamixelAXControl_8cpp.md#define-addr-model-number)** |
| **[ADDR_FIRMWARE_VERSION](Files/DynamixelAXControl_8cpp.md#define-addr-firmware-version)** |
| **[ADDR_ID](Files/DynamixelAXControl_8cpp.md#define-addr-id)** |
| **[ADDR_BAUDRATE](Files/DynamixelAXControl_8cpp.md#define-addr-baudrate)** |
| **[ADDR_RETURN_DELAY_TIME](Files/DynamixelAXControl_8cpp.md#define-addr-return-delay-time)** |
| **[ADDR_CW_ANGLE_LIMIT](Files/DynamixelAXControl_8cpp.md#define-addr-cw-angle-limit)** |
| **[ADDR_CCW_ANGLE_LIMIT](Files/DynamixelAXControl_8cpp.md#define-addr-ccw-angle-limit)** |
| **[ADDR_MAX_TEMPERATURE](Files/DynamixelAXControl_8cpp.md#define-addr-max-temperature)** |
| **[ADDR_MIN_VOLTAJE](Files/DynamixelAXControl_8cpp.md#define-addr-min-voltaje)** |
| **[ADDR_MAX_VOLTAJE](Files/DynamixelAXControl_8cpp.md#define-addr-max-voltaje)** |
| **[ADDR_MAX_TORQUE](Files/DynamixelAXControl_8cpp.md#define-addr-max-torque)** |
| **[ADDR_STATUS_RETURN_LIMIT](Files/DynamixelAXControl_8cpp.md#define-addr-status-return-limit)** |
| **[ADDR_ALARM_LED](Files/DynamixelAXControl_8cpp.md#define-addr-alarm-led)** |
| **[ADDR_SHUTDOWN](Files/DynamixelAXControl_8cpp.md#define-addr-shutdown)** |
| **[ADDR_TORQUE_ENABLE](Files/DynamixelAXControl_8cpp.md#define-addr-torque-enable)** |
| **[ADDR_LED](Files/DynamixelAXControl_8cpp.md#define-addr-led)** |
| **[ADDR_GOAL_POSITION](Files/DynamixelAXControl_8cpp.md#define-addr-goal-position)** |
| **[ADDR_MOVING_SPEED](Files/DynamixelAXControl_8cpp.md#define-addr-moving-speed)** |
| **[ADDR_TORQUE_LIMIT](Files/DynamixelAXControl_8cpp.md#define-addr-torque-limit)** |
| **[ADDR_PRESENT_POSITION](Files/DynamixelAXControl_8cpp.md#define-addr-present-position)** |
| **[ADDR_PRESENT_SPEED](Files/DynamixelAXControl_8cpp.md#define-addr-present-speed)** |
| **[ADDR_PRESENT_LOAD](Files/DynamixelAXControl_8cpp.md#define-addr-present-load)** |
| **[ADDR_PRESENT_VOLTAJE](Files/DynamixelAXControl_8cpp.md#define-addr-present-voltaje)** |
| **[ADDR_PRESENT_TEMPERATURE](Files/DynamixelAXControl_8cpp.md#define-addr-present-temperature)** |
| **[ADDR_REGISTERED](Files/DynamixelAXControl_8cpp.md#define-addr-registered)** |
| **[ADDR_MOVING](Files/DynamixelAXControl_8cpp.md#define-addr-moving)** |
| **[ADDR_LOCK](Files/DynamixelAXControl_8cpp.md#define-addr-lock)** |
| **[ADDR_PUNCH](Files/DynamixelAXControl_8cpp.md#define-addr-punch)** |
| **[MAX_ANGLE_LIMIT](Files/DynamixelAXControl_8cpp.md#define-max-angle-limit)** |
| **[MIN_ANGLE_LIMIT](Files/DynamixelAXControl_8cpp.md#define-min-angle-limit)** |
| **[MIN_SPEED](Files/DynamixelAXControl_8cpp.md#define-min-speed)** |
| **[MAX_JOINT_SPEED](Files/DynamixelAXControl_8cpp.md#define-max-joint-speed)** |
| **[MAX_WHEEL_SPEED](Files/DynamixelAXControl_8cpp.md#define-max-wheel-speed)** |
| **[HEADER_MESSAGE](Files/DynamixelAXControl_8cpp.md#define-header-message)** |

---

## Detailed Description

Implementación de la clase [DynamixelAXControl](Classes/classDynamixelAXControl.md) (control de motores Dynamixel AX). 

* **Author**: Jose Manuel Plascencia Ramos  
* **Version**: 1.0  
* **Date**: 2025-04-01  

Contiene la lógica de bajo nivel para comunicación, conversión de unidades y manejo de modos.

---

## Macros Documentation

### define ADDR_MODEL_NUMBER

```cpp
#define ADDR_MODEL_NUMBER 0

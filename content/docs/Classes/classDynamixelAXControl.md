---
title: "DynamixelAXControl.h"
linkTitle: "DynamixelAXControl.h"
summary: "Header de la clase DynamixelAXControl para control de motores Dynamixel de la serie AX."
description: "Header de la clase DynamixelAXControl para control de motores Dynamixel de la serie AX."
weight: 10
---



Constructor que asocia el controlador a un motor específico.

```cpp
DynamixelManager manager("/dev/ttyUSB0", 57600, 1.0);
DynamixelAXControl ax_controller(&manager, 1); // Controla motor con ID=1
```

---

## Direcciones de Memoria y Constantes (Tabla de Control AX)

```cpp
// Registros EEPROM
#define ADDR_MODEL_NUMBER           0
#define ADDR_FIRMWARE_VERSION        2
#define ADDR_ID                     3
#define ADDR_BAUDRATE               4
#define ADDR_RETURN_DELAY_TIME      5
#define ADDR_CW_ANGLE_LIMIT         6
#define ADDR_CCW_ANGLE_LIMIT        8
#define ADDR_MAX_TEMPERATURE        11
#define ADDR_MIN_VOLTAJE            12
#define ADDR_MAX_VOLTAJE            13
#define ADDR_MAX_TORQUE             14
#define ADDR_STATUS_RETURN_LIMIT    16
#define ADDR_ALARM_LED              17
#define ADDR_SHUTDOWN               18

// Registros RAM
#define ADDR_TORQUE_ENABLE          24
#define ADDR_LED                    25
#define ADDR_GOAL_POSITION         30
#define ADDR_MOVING_SPEED           32
#define ADDR_TORQUE_LIMIT           34
#define ADDR_PRESENT_POSITION      36
#define ADDR_PRESENT_SPEED          38
#define ADDR_PRESENT_LOAD           40
#define ADDR_PRESENT_VOLTAJE        42
#define ADDR_PRESENT_TEMPERATURE    43
#define ADDR_REGISTERED             44
#define ADDR_MOVING                 46
#define ADDR_LOCK                   47
#define ADDR_PUNCH                  48

// Límites y Rangos
#define MIN_ANGLE_LIMIT             0
#define MAX_ANGLE_LIMIT             1023
#define MIN_SPEED                   0
#define MAX_JOINT_SPEED             1023
#define MAX_WHEEL_SPEED             2047
```

---

## Source code

```cpp
#ifndef DYNAMIXEL_CONTROL
#define DYNAMIXEL_CONTROL

#include <string>
#include "DynamixelManagerP1.h"

class DynamixelAXControl {
    
    public:
        // ------------------------- Constructores y Destructor -------------------------
        DynamixelAXControl(DynamixelManagerP1* manager, int idMotor);

        ~DynamixelAXControl();
        
        // ------------------------- Getters -------------------------
        std::string get_message();

        int get_id();
        
        // ------------------------- Configuración, conexion y evaluacion del motor -------------------------

        bool connect(bool home = false);

        bool setWheelMode();

        bool setJointMode(float cwLimit, float ccwLimit, bool degrees = false);
        
        // ------------------------- Control de Movimiento -------------------------

        bool setPosition(float position, bool degrees = false);

        bool setPositionInTime(float position, float time, bool degrees = false);

        bool setSpeed(float speed);

        bool setHome();

        // ------------------------- Lectura de Estados -------------------------

        float getPosition();

        float getSpeed();

        int getVoltaje();

        int getTemperature();

        bool isMoving();

    private:
        // ------------------------- Funciones de conversion -------------------------

        int convertAngleTOint(float angle, bool degrees);

        float convertIntTOangle(int value);

        int convertRADStoInt(float radps);

        float convertINTtoRADS(int value);

        // ------------------------- Validacion y limites -------------------------
        int clamp(int value, int minLimit, int maxLimit);

        bool calculateSpeed(float goal_angle, float time);

        bool setCWAngleLimit(int nlimit);

        bool setCCWAngleLimit(int nlimit);
        
        // ------------------------- Variables privadas -------------------------

        DynamixelManagerP1* control;

        std::string sMessage;

        int idMotor;

        bool bWheelMode;

        bool bInvertido;

        int nCwlimit = 0;

        int nCcwlimit = 0;
};
#endif
```

---

Updated on 2026-10-01 at 16:15:00 -0600

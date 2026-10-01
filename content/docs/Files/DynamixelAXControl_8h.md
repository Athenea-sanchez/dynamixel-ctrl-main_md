---
title: "DynamixelAXControl.h"
linkTitle: "DynamixelAXControl.h"
summary: "Header de la clase DynamixelAXControl."
description: "Header de la clase DynamixelAXControl."
weight: 10
---

# DynamixelAXControl.h

## Classes

| Name | Description |
| ---- | ----------- |
| **[DynamixelAXControl](Classes/classDynamixelAXControl.md)** | Controlador especializado para motores Dynamixel de la serie AX (AX-12A, AX-18F, etc.). |

---

## Source code

```cpp
#ifndef DYNAMIXEL_CONTROL
#define DYNAMIXEL_CONTROL

#include <string>
#include "DynamixelManagerP1.h"


class DynamixelAXControl{
    
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

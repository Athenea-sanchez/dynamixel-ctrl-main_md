---
title: /home/arrgusr/Downloads/dynamixel-ctrl-main/drivers/DriverAX/include/DynamixelAXControl.h
summary: Constructor que asocia el controlador a un motor específico. 

---

# /home/arrgusr/Downloads/dynamixel-ctrl-main/drivers/DriverAX/include/DynamixelAXControl.h



Constructor que asocia el controlador a un motor específico. [DynamixelManager](Classes/classDynamixelManager.md) manager("/dev/ttyUSB0", 57600, 1.0); [DynamixelAXControl](Classes/classDynamixelAXControl.md) ax_controller(&manager, 1); // Controla motor con ID=1 ```cpp


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
```

_Filename: /home/arrgusr/Downloads/dynamixel-ctrl-main/drivers/DriverAX/include/DynamixelAXControl.h_

-------------------------------

Updated on 2026-09-29 at 16:14:57 -0600

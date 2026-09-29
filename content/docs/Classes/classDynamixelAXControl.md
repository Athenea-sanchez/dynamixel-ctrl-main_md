---
title: DynamixelAXControl
summary: Controlador especializado para motores Dynamixel de la serie AX (AX-12A, AX-18F, etc.). 

---

# DynamixelAXControl



Controlador especializado para motores Dynamixel de la serie AX (AX-12A, AX-18F, etc.).  [More...](#detailed-description)


`#include <DynamixelAXControl.h>`

## Public Functions

|                | Name           |
| -------------- | -------------- |
| | **[DynamixelAXControl](Classes/classDynamixelAXControl.md#function-dynamixelaxcontrol)**([DynamixelManagerP1](Classes/classDynamixelManagerP1.md) * manager, int idMotor) |
| | **[~DynamixelAXControl](Classes/classDynamixelAXControl.md#function-~dynamixelaxcontrol)**()<br>Destructor: Libera recursos (no cierra la conexión del manager).  |
| std::string | **[get_message](Classes/classDynamixelAXControl.md#function-get-message)**() |
| int | **[get_id](Classes/classDynamixelAXControl.md#function-get-id)**()<br>Obtiene el ID del motor asociado.  |
| bool | **[connect](Classes/classDynamixelAXControl.md#function-connect)**(bool home =false)<br>Establece conexión con el motor y opcionalmente lo mueve a posición "home".  |
| bool | **[setWheelMode](Classes/classDynamixelAXControl.md#function-setwheelmode)**()<br>Configura el motor en modo "rueda" (rotación continua).  |
| bool | **[setJointMode](Classes/classDynamixelAXControl.md#function-setjointmode)**(float cwLimit, float ccwLimit, bool degrees =false)<br>Configura el motor en modo "articulación" (posición angular limitada).  |
| bool | **[setPosition](Classes/classDynamixelAXControl.md#function-setposition)**(float position, bool degrees =false)<br>Mueve el motor a una posición específica.  |
| bool | **[setPositionInTime](Classes/classDynamixelAXControl.md#function-setpositionintime)**(float position, float time, bool degrees =false)<br>Mueve el motor a una posición específica.  |
| bool | **[setSpeed](Classes/classDynamixelAXControl.md#function-setspeed)**(float speed)<br>Establece la velocidad de movimiento (afecta a [setPosition()](Classes/classDynamixelAXControl.md#function-setposition)).  |
| bool | **[setHome](Classes/classDynamixelAXControl.md#function-sethome)**()<br>Coloca al motor en la posicion home 0 (512 en valor del motor)  |
| float | **[getPosition](Classes/classDynamixelAXControl.md#function-getposition)**()<br>Obtiene la posición actual del motor.  |
| float | **[getSpeed](Classes/classDynamixelAXControl.md#function-getspeed)**()<br>Obtiene la velocidad actual del motor.  |
| int | **[getVoltaje](Classes/classDynamixelAXControl.md#function-getvoltaje)**()<br>Lee el voltaje de entrada del motor.  |
| int | **[getTemperature](Classes/classDynamixelAXControl.md#function-gettemperature)**()<br>Lee la temperatura interna del motor.  |
| bool | **[isMoving](Classes/classDynamixelAXControl.md#function-ismoving)**()<br>Verifica si el motor está en movimiento.  |

## Detailed Description

```cpp
class DynamixelAXControl;
```

Controlador especializado para motores Dynamixel de la serie AX (AX-12A, AX-18F, etc.). 

**Warning**: Esta clase no gestiona la conexión serial (debe inyectarse un [DynamixelManager](Classes/classDynamixelManager.md) válido). 

Proporciona una interfaz de alto nivel para manejar motores AX usando un [DynamixelManager](Classes/classDynamixelManager.md) existente. 

## Public Functions Documentation

### function DynamixelAXControl

```cpp
DynamixelAXControl(
    DynamixelManagerP1 * manager,
    int idMotor
)
```


### function ~DynamixelAXControl

```cpp
~DynamixelAXControl()
```

Destructor: Libera recursos (no cierra la conexión del manager). 

**Note**: El [DynamixelManager](Classes/classDynamixelManager.md) debe vivir más que este objeto. 

### function get_message

```cpp
std::string get_message()
```


### function get_id

```cpp
int get_id()
```

Obtiene el ID del motor asociado. 

**Return**: int ID configurado en el constructor (1-253). 

### function connect

```cpp
bool connect(
    bool home =false
)
```

Establece conexión con el motor y opcionalmente lo mueve a posición "home". 

**Parameters**: 

  * **home** Si es true, ejecuta un movimiento a home después de conectar. 


**Exceptions**: 

  * **std::runtime_error** Si el motor no responde. 


**Return**: 

  * true Si la conexión y homing (si aplica) fueron exitosos. 
  * false Si falla en alguna parte de la conexion. 


**Note**: 

  * Al terminar la operacion se asignan mensajes para los limites de movimiento y velocidad actual. 
  * consultar el valor de dxl_comm_result del manager y get_message() para consultar el mensaje de error asignado. 


### function setWheelMode

```cpp
bool setWheelMode()
```

Configura el motor en modo "rueda" (rotación continua). 

**Return**: true Si el cambio de modo fue exitoso. 

**Warning**: Sobrescribe los límites de posición. Usar [setJointMode()](Classes/classDynamixelAXControl.md#function-setjointmode) para volver a modo articulación. 

### function setJointMode

```cpp
bool setJointMode(
    float cwLimit,
    float ccwLimit,
    bool degrees =false
)
```

Configura el motor en modo "articulación" (posición angular limitada). 

**Parameters**: 

  * **cwLimit** Límite horario (en radianes o grados, segun el valor de 'degrees'). 
  * **ccwLimit** Límite antihorario (en radianes o grados, segun el valor de 'degrees'). 
  * **degrees** Si true, los límites se interpretan en grados (150- -150). Si false, en Radianes. 


**Return**: true Si la configuración fue exitosa. 

**Note**: Los valores típicos en grados para la serie AX es de 150 a -150 en grados. 

### function setPosition

```cpp
bool setPosition(
    float position,
    bool degrees =false
)
```

Mueve el motor a una posición específica. 

**Parameters**: 

  * **position** Posición objetivo (en radianes o grados, segun el valor de 'degrees'). 
  * **degrees** Si true, los límites se interpretan en grados (150- -150). Si false, en Radianes. 


**See**: [getPosition()](Classes/classDynamixelAXControl.md#function-getposition), [setJointMode()](Classes/classDynamixelAXControl.md#function-setjointmode)

**Return**: true Si el comando se envió correctamente (no bloqueante; ver getMoving()). 

### function setPositionInTime

```cpp
bool setPositionInTime(
    float position,
    float time,
    bool degrees =false
)
```

Mueve el motor a una posición específica. 

**Parameters**: 

  * **position** Posición objetivo (en radianes o grados, segun el valor de 'degrees'). 
  * **time** Tiempo en el que se alcanzara el objetivo (en segundos). 
  * **degrees** Si true, los límites se interpretan en grados (150- -150). Si false, en Radianes. 


**See**: [getPosition()](Classes/classDynamixelAXControl.md#function-getposition), [setJointMode()](Classes/classDynamixelAXControl.md#function-setjointmode)

**Return**: true Si el comando se envió correctamente (no bloqueante; ver getMoving()). 

### function setSpeed

```cpp
bool setSpeed(
    float speed
)
```

Establece la velocidad de movimiento (afecta a [setPosition()](Classes/classDynamixelAXControl.md#function-setposition)). 

**Parameters**: 

  * **speed** Velocidad (rango depende del modo):

* Modo articulación: 0 - 11.89127016 (0-1023 en valor del servo)
* Modo rueda: 11.89127016 a -11.89127016 (0-11.89127016 CW, 0 a -11.89127016 CCW). 


**Return**: true Si el parámetro fue aceptado. 

**Note**: Los valores se encuentran en la unidad de rads/s 

### function setHome

```cpp
bool setHome()
```

Coloca al motor en la posicion home 0 (512 en valor del motor) 

**Return**: 

  * true Si se completo el movimiento exitosamente. 
  * false Sí falló al llevar el movimiento. 


### function getPosition

```cpp
float getPosition()
```

Obtiene la posición actual del motor. 

**Return**: devuelve el valor de la posicion acutal del servo en radianes 

### function getSpeed

```cpp
float getSpeed()
```

Obtiene la velocidad actual del motor. 

**Return**: float Velocidad (interpretación igual que [setSpeed()](Classes/classDynamixelAXControl.md#function-setspeed)). 

### function getVoltaje

```cpp
int getVoltaje()
```

Lee el voltaje de entrada del motor. 

**Return**: Devuelve el voltaje según los valores especificados en la memoria del motor 

**Note**: Consultar el manual del motor

**Warning**: 

  * No se han implementado funciones de conversion a este metodo. 
  * no se han implementado funciones de conversion retorna valores del motor. 


### function getTemperature

```cpp
int getTemperature()
```

Lee la temperatura interna del motor. 

**Return**: Devuelve la temperatura según los valores especificados en la memoria del motor 

**Note**: Consultar el manual del motor

**Warning**: 

  * No se han implementado funciones de conversion a este metodo. 
  * no se han implementado funciones de conversion retorna valores del motor. 


### function isMoving

```cpp
bool isMoving()
```

Verifica si el motor está en movimiento. 

**Return**: 

  * true Si el motor está ejecutando un movimiento ([setPosition()](Classes/classDynamixelAXControl.md#function-setposition) pendiente). 
  * false Sí el motor no está ejecutando un movimiento ([setPosition()](Classes/classDynamixelAXControl.md#function-setposition) completado). 


-------------------------------

Updated on 2026-09-29 at 16:14:57 -0600
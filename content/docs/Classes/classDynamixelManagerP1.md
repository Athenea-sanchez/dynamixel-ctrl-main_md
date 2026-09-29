---
title: DynamixelManagerP1

---

# DynamixelManagerP1





## Public Functions

|                | Name           |
| -------------- | -------------- |
| | **[DynamixelManagerP1](Classes/classDynamixelManagerP1.md#function-dynamixelmanagerp1)**(const std::string & sPort, int nBaudrate)<br>Constructor principal para inicializar la conexión con los motores.  |
| | **[~DynamixelManagerP1](Classes/classDynamixelManagerP1.md#function-~dynamixelmanagerp1)**()<br>Destructor: Libera recursos y cierra la conexión.  |
| int | **[get_dxl_comm_result](Classes/classDynamixelManagerP1.md#function-get-dxl-comm-result)**()<br>Obtiene el resultado de la última operación de comunicación.  |
| uint8_t | **[get_dxl_error](Classes/classDynamixelManagerP1.md#function-get-dxl-error)**()<br>Obtiene el último error reportado por un motor Dynamixel.  |
| bool | **[isConnect](Classes/classDynamixelManagerP1.md#function-isconnect)**()<br>Verifica el estado de la conexión con el puerto serial.  |
| int | **[get_baudrate](Classes/classDynamixelManagerP1.md#function-get-baudrate)**()<br>Da el valor de baudrate con el que se configuro el objeto.  |
| std::string | **[get_port](Classes/classDynamixelManagerP1.md#function-get-port)**()<br>Proporciona el nombre del puerto que se utilizado por el objeto.  |
| dynamixel::PortHandler * | **[getPortHandler](Classes/classDynamixelManagerP1.md#function-getporthandler)**()<br>Obtiene el manejador del puerto serial (para operaciones avanzadas).  |
| dynamixel::PacketHandler * | **[getPacketHandler](Classes/classDynamixelManagerP1.md#function-getpackethandler)**()<br>Obtiene el manejador de paquetes (para comunicación low-level).  |
| int | **[connect](Classes/classDynamixelManagerP1.md#function-connect)**()<br>Establece conexión con el puerto serial configurado en el constructor.  |
| void | **[disconnect](Classes/classDynamixelManagerP1.md#function-disconnect)**()<br>Cierra la conexión serial y libera recursos.  |
| bool | **[pingServo](Classes/classDynamixelManagerP1.md#function-pingservo)**(int idServo)<br>Verifica si un servo Dynamixel específico está conectado y respondiendo.  |
| bool | **[write1byte](Classes/classDynamixelManagerP1.md#function-write1byte)**(int idServo, int address, int value)<br>Escribe 1 byte (8 bits) en la memoria del servo.  |
| bool | **[write2byte](Classes/classDynamixelManagerP1.md#function-write2byte)**(int idServo, int address, int value)<br>Escribe 2 bytes (16 bits) en la memoria del servo.  |
| bool | **[writeMultiple](Classes/classDynamixelManagerP1.md#function-writemultiple)**(const std::vector< uint8_t > & ids, uint16_t address, uint8_t data_length, const std::vector< std::vector< uint8_t > > & values)<br>Escribe 2 bytes (16 bits) en la memoria del servo.  |
| int | **[read1byte](Classes/classDynamixelManagerP1.md#function-read1byte)**(int idServo, int address)<br>Lee 1 byte (8 bits) de la memoria del servo.  |
| int | **[read2byte](Classes/classDynamixelManagerP1.md#function-read2byte)**(int idServo, int address)<br>Lee 2 bytes (16 bits) de la memoria del servo.  |
| std::map< uint8_t, std::vector< uint8_t > > | **[readMultiple](Classes/classDynamixelManagerP1.md#function-readmultiple)**(const std::vector< uint8_t > & ids, uint16_t address, uint8_t data_length)<br>Escribe 2 bytes (16 bits) en la memoria del servo.  |

## Public Functions Documentation

### function DynamixelManagerP1

```cpp
DynamixelManagerP1(
    const std::string & sPort,
    int nBaudrate
)
```

Constructor principal para inicializar la conexión con los motores. 

Inicializa los manejadores de puerto y paquetes del SDK Dynamixel.

* Configura el puerto serial pero NO lo abre (usar [connect()](Classes/classDynamixelManagerP1.md#function-connect) posteriormente). sPortNombre del puerto serial (ej: "/dev/ttyUSB0" en Linux, "COM3" en Windows). 

nBaudrateVelocidad de comunicación en baudios (ej: 57600, 115200). 

std::runtime_errorSi falla la apertura del puerto. 


### function ~DynamixelManagerP1

```cpp
~DynamixelManagerP1()
```

Destructor: Libera recursos y cierra la conexión. 

Garantiza una desconexión segura:

1. Cierra la conexión serial si está activa (llamando a [disconnect()](Classes/classDynamixelManagerP1.md#function-disconnect)).
2. Libera la memoria de los manejadores del SDK. No lanza excepciones para evitar problemas en el flujo de destrucción. 


### function get_dxl_comm_result

```cpp
int get_dxl_comm_result()
```

Obtiene el resultado de la última operación de comunicación. 

**See**: dynamixel::CommErrorCode 

**Return**: int

* `COMM_SUCCESS` (0) si la operación fue exitosa.
* Código de error específico de Dynamixel en caso de fallo. 

### function get_dxl_error

```cpp
uint8_t get_dxl_error()
```

Obtiene el último error reportado por un motor Dynamixel. 

**Return**: uint8_t Byte de error (consultar manual Dynamixel para bits de error). 

### function isConnect

```cpp
bool isConnect()
```

Verifica el estado de la conexión con el puerto serial. 

**Return**: 

  * true Si el puerto está abierto y operativo. 
  * false Si no hay conexion o hay un error de conexión. 


### function get_baudrate

```cpp
int get_baudrate()
```

Da el valor de baudrate con el que se configuro el objeto. 

**Return**: valor entero del baudrate. 

### function get_port

```cpp
std::string get_port()
```

Proporciona el nombre del puerto que se utilizado por el objeto. 

**Return**: cadena con el dispositivo. 

### function getPortHandler

```cpp
dynamixel::PortHandler * getPortHandler()
```

Obtiene el manejador del puerto serial (para operaciones avanzadas). 

**Return**: Puntero a dynamixel::PortHandler. 

**Warning**: Modificar este objeto puede afectar la conexión. 

### function getPacketHandler

```cpp
dynamixel::PacketHandler * getPacketHandler()
```

Obtiene el manejador de paquetes (para comunicación low-level). 

**Return**: Puntero a dynamixel::PacketHandler. 

### function connect

```cpp
int connect()
```

Establece conexión con el puerto serial configurado en el constructor. 

**Exceptions**: 

  * **std::runtime_error** Si el puerto no existe o está en uso. 


**Return**: int

* `0` (COMM_SUCCESS) si la conexión fue exitosa.
* -1 si falla al abrir el puerto.
* -2 si falla al establecer el baud rate de comunicacion. 

**Note**: Realiza un handshake inicial con los motores. 

**Warning**: No es thread-safe. Si se llama desde múltiples hilos, usar mutex. 

### function disconnect

```cpp
void disconnect()
```

Cierra la conexión serial y libera recursos. 

**Warning**: No se pueden enviar comandos después de llamar a este método. 

### function pingServo

```cpp
bool pingServo(
    int idServo
)
```

Verifica si un servo Dynamixel específico está conectado y respondiendo. 

**Parameters**: 

  * **idServo** ID del servo (0-253 para protocolo 2.0, 1-254 para 1.0). 


**Return**: 

  * true Si el servo responde al ping. 
  * false Si hay timeout o error de comunicación (consultar dxl_comm_result para mas detalle). 


### function write1byte

```cpp
bool write1byte(
    int idServo,
    int address,
    int value
)
```

Escribe 1 byte (8 bits) en la memoria del servo. 

**Parameters**: 

  * **idServo** ID del servo destino. 
  * **address** Dirección de memoria (ej: 64 para "Torque Enable"). 
  * **value** Valor a escribir (0-255). 


**See**: Control Table del servo (manual Dynamixel). 

**Return**: 

  * true Si la escritura fue confirmada por el servo. 
  * false Si hubo error de comunicación o el servo rechazó el valor (consultar dxl_comm_result para mas detalle). 


### function write2byte

```cpp
bool write2byte(
    int idServo,
    int address,
    int value
)
```

Escribe 2 bytes (16 bits) en la memoria del servo. 

**Parameters**: 

  * **idServo** ID del servo destino. 
  * **address** Dirección de memoria (ej: 116 para "Goal Position" en AX-12A). 
  * **value** Valor a escribir (0-65535). 


**Return**: bool 

### function writeMultiple

```cpp
bool writeMultiple(
    const std::vector< uint8_t > & ids,
    uint16_t address,
    uint8_t data_length,
    const std::vector< std::vector< uint8_t > > & values
)
```

Escribe 2 bytes (16 bits) en la memoria del servo. 

**Parameters**: 

  * **ids** IDs de los motores a los que se les esc 
  * **address** Direcciones de memoria para cada motor 
  * **data_length** longitud de los datos numero entero en bytes, como es protocolo 1 unicamente puede ser 1 o 2. 
  * **values** Valores a escribir 


**Return**: bool 

### function read1byte

```cpp
int read1byte(
    int idServo,
    int address
)
```

Lee 1 byte (8 bits) de la memoria del servo. 

**Parameters**: 

  * **idServo** ID del servo a consultar. 
  * **address** Dirección de memoria (ej: 63 para "Present Load"). 


**Return**: int Valor leído (0-255) o -1 si hubo error. 

**Warning**: El valor -1 puede indicar error y -2 si no hay conexion. 

### function read2byte

```cpp
int read2byte(
    int idServo,
    int address
)
```

Lee 2 bytes (16 bits) de la memoria del servo. 

**Parameters**: 

  * **idServo** ID del servo a consultar. 
  * **address** Dirección de memoria (ej: 126 para "Present Position"). 


**Return**: int Valor leído (0-65535), -2 si no hay conexion y -1 si hubo error. 

### function readMultiple

```cpp
std::map< uint8_t, std::vector< uint8_t > > readMultiple(
    const std::vector< uint8_t > & ids,
    uint16_t address,
    uint8_t data_length
)
```

Escribe 2 bytes (16 bits) en la memoria del servo. 

**Parameters**: 

  * **ids** lista de ids a los cuales se leeran los datos. 
  * **address** Dirección de memoria (ej: 116 para "Goal Position" en AX-12A). 
  * **data_length** longitud de los datos numero entero en bytes, como es protocolo 1 unicamente puede ser 1 o 2. 


**Return**: map con los datos obtenidos la ID es la key. 

-------------------------------

Updated on 2026-09-29 at 16:14:57 -0600
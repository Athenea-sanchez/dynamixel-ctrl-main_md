---
title: "DynamixelManagerP1"
linkTitle: "DynamixelManagerP1"
summary: "Manejador principal de puerto serial y protocolo 1.0 para motores Dynamixel."
description: "Manejador principal de puerto serial y protocolo 1.0 para motores Dynamixel."
weight: 10
---

# DynamixelManagerP1

```cpp
`#include <DynamixelManagerP1.h>`
```

## Public Functions

| Name | Description |
| ---- | ----------- |
| **[DynamixelManagerP1](Classes/classDynamixelManagerP1.md#function-dynamixelmanagerp1)**(const std::string &sPort, int nBaudrate) | Constructor principal para inicializar la conexión con los motores. |
| **[~DynamixelManagerP1](Classes/classDynamixelManagerP1.md#function-~dynamixelmanagerp1)**() | Destructor: Libera recursos y cierra la conexión. |
| int **[get_dxl_comm_result](Classes/classDynamixelManagerP1.md#function-get-dxl-comm-result)**() | Obtiene el resultado de la última operación de comunicación. |
| uint8_t **[get_dxl_error](Classes/classDynamixelManagerP1.md#function-get-dxl-error)**() | Obtiene el último error reportado por un motor Dynamixel. |
| bool **[isConnect](Classes/classDynamixelManagerP1.md#function-isconnect)**() | Verifica el estado de la conexión con el puerto serial. |
| int **[get_baudrate](Classes/classDynamixelManagerP1.md#function-get-baudrate)**() | Da el valor de baudrate con el que se configuró el objeto. |
| std::string **[get_port](Classes/classDynamixelManagerP1.md#function-get-port)**() | Proporciona el nombre del puerto utilizado por el objeto. |
| dynamixel::PortHandler * **[getPortHandler](Classes/classDynamixelManagerP1.md#function-getporthandler)**() | Obtiene el manejador del puerto serial (para operaciones avanzadas). |
| dynamixel::PacketHandler * **[getPacketHandler](Classes/classDynamixelManagerP1.md#function-getpackethandler)**() | Obtiene el manejador de paquetes (para comunicación low-level). |
| int **[connect](Classes/classDynamixelManagerP1.md#function-connect)**() | Establece conexión con el puerto serial configurado en el constructor. |
| void **[disconnect](Classes/classDynamixelManagerP1.md#function-disconnect)**() | Cierra la conexión serial y libera recursos. |
| bool **[pingServo](Classes/classDynamixelManagerP1.md#function-pingservo)**(int idServo) | Verifica si un servo Dynamixel específico está conectado y respondiendo. |
| bool **[write1byte](Classes/classDynamixelManagerP1.md#function-write1byte)**(int idServo, int address, int value) | Escribe 1 byte (8 bits) en la memoria del servo. |
| bool **[write2byte](Classes/classDynamixelManagerP1.md#function-write2byte)**(int idServo, int address, int value) | Escribe 2 bytes (16 bits) en la memoria del servo. |
| bool **[writeMultiple](Classes/classDynamixelManagerP1.md#function-writemultiple)**(const std::vector<uint8_t> &ids, uint16_t address, uint8_t data_length, const std::vector<std::vector<uint8_t>> &values) | Escribe datos de forma sincrónica/múltiple en varios servos. |
| int **[read1byte](Classes/classDynamixelManagerP1.md#function-read1byte)**(int idServo, int address) | Lee 1 byte (8 bits) de la memoria del servo. |
| int **[read2byte](Classes/classDynamixelManagerP1.md#function-read2byte)**(int idServo, int address) | Lee 2 bytes (16 bits) de la memoria del servo. |
| std::map<uint8_t, std::vector<uint8_t>> **[readMultiple](Classes/classDynamixelManagerP1.md#function-readmultiple)**(const std::vector<uint8_t> &ids, uint16_t address, uint8_t data_length) | Lee datos de múltiples servos simultáneamente. |

---

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

**Parameters**:
* **sPort**: Nombre del puerto serial (ej: `/dev/ttyUSB0` en Linux, `COM3` en Windows).
* **nBaudrate**: Velocidad de comunicación en baudios (ej: 57600, 115200).

**Exceptions**:
* **std::runtime_error**: Si falla la inicialización del puerto.

**Note**: Configura el puerto serial pero NO lo abre directamente; se debe usar [connect()](Classes/classDynamixelManagerP1.md#function-connect) posteriormente.

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

**See**: `dynamixel::CommErrorCode`

**Return**: `int`
* `COMM_SUCCESS` (0) si la operación fue exitosa.
* Código de error específico de Dynamixel en caso de fallo.

### function get_dxl_error

```cpp
uint8_t get_dxl_error()
```

Obtiene el último error reportado por un motor Dynamixel.

**Return**: `uint8_t` Byte de error (consultar el manual de Dynamixel para los bits de error específicos).

### function isConnect

```cpp
bool isConnect()
```

Verifica el estado de la conexión con el puerto serial.

**Return**:
* `true`: Si el puerto está abierto y operativo.
* `false`: Si no hay conexión o hay un error de conexión.

### function get_baudrate

```cpp
int get_baudrate()
```

Da el valor de baudrate con el que se configuró el objeto.

**Return**: Valor entero del baudrate.

### function get_port

```cpp
std::string get_port()
```

Proporciona el nombre del puerto utilizado por el objeto.

**Return**: Cadena de texto con el identificador del dispositivo (puerto).

### function getPortHandler

```cpp
dynamixel::PortHandler * getPortHandler()
```

Obtiene el manejador del puerto serial (para operaciones avanzadas).

**Return**: Puntero a `dynamixel::PortHandler`.

**Warning**: Modificar directamente este objeto puede afectar la estabilidad de la conexión.

### function getPacketHandler

```cpp
dynamixel::PacketHandler * getPacketHandler()
```

Obtiene el manejador de paquetes (para comunicación low-level).

**Return**: Puntero a `dynamixel::PacketHandler`.

### function connect

```cpp
int connect()
```

Establece conexión con el puerto serial configurado en el constructor.

**Exceptions**:
* **std::runtime_error**: Si el puerto no existe o está en uso.

**Return**: `int`
* `0` (`COMM_SUCCESS`): Si la conexión fue exitosa.
* `-1`: Si falla al abrir el puerto.
* `-2`: Si falla al establecer el baud rate de comunicación.

**Note**: Realiza un handshake inicial con los motores.

**Warning**: No es thread-safe. Si se llama desde múltiples hilos, implementar control por mutex.

### function disconnect

```cpp
void disconnect()
```

Cierra la conexión serial y libera recursos.

**Warning**: No se pueden enviar comandos tras llamar a este método.

### function pingServo

```cpp
bool pingServo(
    int idServo
)
```

Verifica si un servo Dynamixel específico está conectado y respondiendo.

**Parameters**:
* **idServo**: ID del servo (1-254 para protocolo 1.0, 0-253 para protocolo 2.0).

**Return**:
* `true`: Si el servo responde al ping.
* `false`: Si hay timeout o error de comunicación (consultar `dxl_comm_result` para más detalle).

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
* **idServo**: ID del servo destino.
* **address**: Dirección de memoria (ej: 64 para "Torque Enable").
* **value**: Valor a escribir (0-255).

**See**: Control Table del servo en el manual de Dynamixel.

**Return**:
* `true`: Si la escritura fue confirmada por el servo.
* `false`: Si hubo error de comunicación o el servo rechazó el valor (consultar `dxl_comm_result` para más detalle).

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
* **idServo**: ID del servo destino.
* **address**: Dirección de memoria (ej: 30 para "Goal Position" en serie AX).
* **value**: Valor a escribir (0-65535).

**Return**: `bool` `true` si la escritura fue exitosa, `false` en caso contrario.

### function writeMultiple

```cpp
bool writeMultiple(
    const std::vector< uint8_t > & ids,
    uint16_t address,
    uint8_t data_length,
    const std::vector< std::vector< uint8_t > > & values
)
```

Escribe datos de forma múltiple/sincrónica en la memoria de varios servos.

**Parameters**:
* **ids**: Lista de IDs de los motores a los cuales escribir.
* **address**: Dirección de memoria objetivo.
* **data_length**: Longitud de los datos en bytes (para protocolo 1 únicamente puede ser 1 o 2).
* **values**: Matriz con los valores en bytes correspondientes para cada motor.

**Return**: `bool` `true` si la instrucción fue transmitida correctamente.

### function read1byte

```cpp
int read1byte(
    int idServo,
    int address
)
```

Lee 1 byte (8 bits) de la memoria del servo.

**Parameters**:
* **idServo**: ID del servo a consultar.
* **address**: Dirección de memoria (ej: 43 para "Present Voltage").

**Return**: `int` Valor leído (0-255), `-1` si hubo un error de comunicación o `-2` si no hay conexión activa.

### function read2byte

```cpp
int read2byte(
    int idServo,
    int address
)
```

Lee 2 bytes (16 bits) de la memoria del servo.

**Parameters**:
* **idServo**: ID del servo a consultar.
* **address**: Dirección de memoria (ej: 36 para "Present Position").

**Return**: `int` Valor leído (0-65535), `-1` si hubo un error de comunicación o `-2` si no hay conexión activa.

### function readMultiple

```cpp
std::map< uint8_t, std::vector< uint8_t > > readMultiple(
    const std::vector< uint8_t > & ids,
    uint16_t address,
    uint8_t data_length
)
```

Lee datos de la memoria de múltiples servos en una sola consulta.

**Parameters**:
* **ids**: Lista de IDs a los cuales se les leerán los datos.
* **address**: Dirección de memoria inicial.
* **data_length**: Longitud de los datos a leer en bytes (para protocolo 1 únicamente puede ser 1 o 2).

**Return**: `std::map<uint8_t, std::vector<uint8_t>>` Mapa donde la clave es el ID del servo y el valor es el vector de bytes leídos.

-------------------------------

Updated on 2026-10-01 at 16:15:00 -0600

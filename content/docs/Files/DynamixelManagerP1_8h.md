---
title: drivers/DriverAX/include/DynamixelManagerP1.h

---

# drivers/DriverAX/include/DynamixelManagerP1.h



## Classes

|                | Name           |
| -------------- | -------------- |
| class | **[DynamixelManagerP1](Classes/classDynamixelManagerP1.md)**  |




## Source code

```cpp

#ifndef DYNAMIXEL_SDK_CONTROL_P1
#define DYNAMIXEL_SDK_CONTROL_P1

#include "dynamixel_sdk/dynamixel_sdk.h"
#include <string>
#include <memory>

class DynamixelManagerP1
{
    public:

        // ------------------------->> Constructor y Destructor <<-------------------------
        DynamixelManagerP1(const std::string& sPort, int nBaudrate);
        
        ~DynamixelManagerP1();

        // ------------------------->> Getters (Accesores) <<-------------------------
        int get_dxl_comm_result();

        uint8_t get_dxl_error();
        
        bool isConnect();

        int get_baudrate();
        
        std::string get_port();

        dynamixel::PortHandler*getPortHandler();
        
        dynamixel::PacketHandler*getPacketHandler();

        // -------------------------->>  Conectividad  <<--------------------------
        int connect();

        void disconnect();

        bool pingServo(int idServo);

        // -------------------------->>  Operaciones de escritura  <<--------------------------
        bool write1byte(int idServo, int address, int value);

        bool write2byte(int idServo, int address, int value);

        bool writeMultiple(const std::vector<uint8_t>& ids, uint16_t address, uint8_t data_length, const std::vector<std::vector<uint8_t>>& values);
        
        // -------------------------->>  Operaciones de lectura  <<--------------------------
        int read1byte(int idServo, int address);
        
        int read2byte(int idServo, int address);

        std::map<uint8_t, std::vector<uint8_t>> readMultiple(const std::vector<uint8_t>& ids, uint16_t address, uint8_t data_length);
        

    private:

        dynamixel::PortHandler* portHandler;   
        dynamixel::PacketHandler* packetHandler; 
    
        bool bConnection;  
    
        uint8_t dxl_error = 0; 
        int dxl_comm_result = 0; 
        int baudrate = 0;  
        std::string port = "";  
};
#endif
```


-------------------------------

Updated on 2026-09-29 at 16:14:57 -0600

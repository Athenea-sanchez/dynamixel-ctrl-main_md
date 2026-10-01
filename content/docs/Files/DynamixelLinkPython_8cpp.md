---
title: "DynamixelLinkPython.cpp"
linkTitle: "DynamixelLinkPython.cpp"
summary: "Módulo Python para control de motores Dynamixel (vía pybind11)."
description: "Módulo Python para control de motores Dynamixel (vía pybind11)."
weight: 10
---

# DynamixelLinkPython.cpp

Módulo Python para control de motores Dynamixel (vía pybind11). [More...](#detailed-description)

## Functions

| | Name |
| --- | --- |
| | **[PYBIND11_MODULE](Files/DynamixelLinkPython_8cpp.md#function-pybind11-module)**([DynamixelAXControl](Classes/classDynamixelAXControl.md) , m ) |

## Detailed Description

Módulo Python para control de motores Dynamixel (vía pybind11).

**Warning**: Para uso unicamente con protocolo 1.0.

Expone las clases [DynamixelAXControl](Classes/classDynamixelAXControl.md) a Python.

## Functions Documentation

### function PYBIND11_MODULE

```cpp
PYBIND11_MODULE(
    DynamixelAXControl ,
    m 
)
```

## Source code

```cpp
#include <pybind11/pybind11.h>
#include "DynamixelAXControl.h"
#include "DynamixelManagerP1.h"

namespace py = pybind11;

PYBIND11_MODULE(DynamixelAXControl,m){
    py::class_<DynamixelAXControl>(m , "DynamixelAXControl")
        .def(py::init<DynamixelManagerP1* , int>())
        .def("get_message",&DynamixelAXControl::get_message)
        .def("get_id",&DynamixelAXControl::get_id)
        .def("connect",&DynamixelAXControl::connect, py::arg("home")=false)
        .def("setWheelMode",&DynamixelAXControl::setWheelMode)
        .def("setJointMode",&DynamixelAXControl::setJointMode, py::arg("cwLimit"), py::arg("ccwLimit"), py::arg("degrees")=false)
        .def("setPosition",&DynamixelAXControl::setPosition, py::arg("position"), py::arg("degrees")=false)
        .def("setPositionInTime",&DynamixelAXControl::setPositionInTime, py::arg("position"), py::arg("time"), py::arg("degrees")=false)
        .def("setSpeed",&DynamixelAXControl::setSpeed)
        .def("setHome",&DynamixelAXControl::setHome)
        .def("getPosition",&DynamixelAXControl::getPosition)
        .def("getSpeed",&DynamixelAXControl::getSpeed)
        .def("getVoltaje",&DynamixelAXControl::getVoltaje)
        .def("getTemperature",&DynamixelAXControl::getTemperature)
        .def("isMoving",&DynamixelAXControl::isMoving);
}
```

-------------------------------

Updated on 2026-09-29 at 16:14:57 -0600

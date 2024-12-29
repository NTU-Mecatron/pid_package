# A simple C++ PID controller package

## Class constructor and method

```cpp
    PID ( double Kp, double Ki, double Kd, double dt, double max, double min );
```

```cpp
    double calculate ( double setpoint, double current );
```

## Installation

```bash
cd ~/catkin_ws/src
git clone -b ros1 https://github.com/NTU-Mecatron/pid_package
```

## Example usage

For `.hpp`/`.h` file:

```cpp
#include <pid_package/pid.h>

class YourClass {
public:
    YourClass();

private:
    PID your_pid_ = PID(0,0,0,0,0,0);
};
```

For `.cpp` file:

```cpp
#include "your_package/your_class.hpp"
YourClass::YourClass() {
    your_pid_ = PID(1, 0.1, 0.01, 0.01, 100, -100);
}

void YourClass::yourCallback() {
    double setpoint = 10;
    double current = 5;
    double output = your_pid_.calculate(setpoint, current);
}
```

You can use `float` type for the PID controller as well.

## CMakelists.txt

Modify your `CMakeLists.txt` file to include the following:

```cmake
find_package(pid_package REQUIRED)
```

## package.xml

Modify your `package.xml` file to include the following:

```xml
<build_depend>pid_package</build_depend>
<exec_depend>pid_package</exec_depend>
```


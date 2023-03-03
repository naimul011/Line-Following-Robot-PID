# Arduino Line Following Robot using PID System
This is a simple Arduino code for a line following robot using a PID system. The robot uses QTR Sensors to detect the line and make necessary corrections using a PID algorithm.

## Components
Arduino Board
QTR Sensors
DC Motors
L293D Motor Driver
Chassis
Code Explanation
The code is well commented to make it easy to understand. Here are the main components:

## Libraries
The code uses the QTRSensors library to read sensor data from the QTR sensors. Ensure that you have the QTRSensors library installed in your Arduino IDE.

## Calibration
To ensure accurate readings from the sensors, the code calibrates the sensors by sliding the sensors across the line or using auto-calibration. During calibration, the robot turns right and left to expose the sensors to the brightest and darkest readings that may be encountered.

## PID Constants
The code uses three constants to implement the PID system:

Kp: The proportional gain, which determines how aggressively the robot should correct its position. Start with a small value that makes the robot follow the line at a slow speed and gradually increase it to adjust the speed.
Kd: The derivative gain, which determines how much the robot should adjust its position based on the rate of change of the error. The value of Kd should be greater than Kp.
Timeout: The maximum amount of time to wait for sensor outputs to go low.
Loop Function
The loop function reads the sensor data and calculates the error. It then uses the PID constants to adjust the speed of the motors based on the error. The robot moves forward with the appropriate speeds.

```c++
// Get calibrated readings along with the line position, refer to the QTR Sensors Arduino Library for more details on line position.
int position = qtrrc.readLine(sensors,QTR_EMITTERS_ON,1); 
int error = position / 3000;

//KID Implementaion
int motorSpeed = Kp * erro + Kd * (error - lastError);
lastError = error;
```
## Circuit Diagram
The circuit diagram for this project is not included in this code. Please refer to the hardware documentation for the circuit diagram.

## Credits
This code was written by Naimul Haque and adapted from the QTR Sensors Arduino Library examples.

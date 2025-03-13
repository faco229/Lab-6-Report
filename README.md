# Lab-6-Report

**Names of People Involved (Group Members):**  
Faith Cox & Quinn Rison 

**Date Submitted:**  
3/12/2025

---

## Introduction / Summary
This lab focuses on the use of ultrasonic sensors for object detection and distance measurement, like systems used in modern vehicles to prevent collisions. The integration of libraries will control the robot's wheels, and a program will be developed to avoid obstacles. Additionally, the lab covers the differences between analog and digital sensors, highlighting their respective signal types and applications. Analog sensors provide a continuous range of values and require analog-to-digital conversion, while digital sensors offer discrete values, commonly represented as 0V or 5V. The ultrasonic sensor, which uses echolocation to measure distance, will be a key component in the collision avoidance system.

---

## Methods / Tests
Before starting the lab, an overview of the TB6612FNG breakout should be covered. The TB6612FNG breakout board features three types of pins: power, input, and output, all clearly labeled on the back of the board. The power pins include VM for motor voltage (2.2V to 13.5V), VCC for logic voltage (2.7V to 5.5V), and GND for the common ground. Input pins consist of STBY for enabling the H-bridges, AIN1/BIN1 and AIN2/BIN2 for determining motor direction, and PWMA/PWMB for controlling motor speed via PWM signals. Output pins, A01/B01 and A02/B02, are used to connect the motors. This configuration allows for efficient control of motor direction and speed using the Arduino.

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Fig1_Bridge%20Motor.jpg" width="300">
  <br>
  <b>Figure 1:</b> Photo of Dual TB6612FNG H-Bridge Motor (https://market.samm.com/sparkfun-motordriver-dual-tb6612fng-with-headers)
</p>

To repeat this lab, the components require a computer running Arduino IDE and the SparkFun Inventor’s Kit, which includes a RedBoard, an ultrasonic sensor, two motors, and a motor driver. 
The task involves familiarizing with the use of an ultrasonic sensor in distance-measuring applications, understanding the functionality of the motor driver, and programming an algorithm to control the movement of two motors. Additionally, a program will be developed to prevent the robot from colliding with objects in front of it.

**Part 1- Learn to Listen**
To start Part 1, the ultrasonic sensor should be connected to the RedBoard as shown in the image below. After, make sure the RedBoard is plugged into the computer and open up Arduino IDE to begin programming. 

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Schematic1_Sensor%20connected%20to%20redboard.jpg" width="500">
  <br>
  <b>Schematic 1:</b> Ultrasonic Sensor connected to Redboard
</p>

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Fig2_sensore%20to%20redboard%20photo.jpg" width="500">
  <br>
  <b>Figure 2:</b> Ultrasonic Sensor connected to Redboard
</p>

The goal of the program is to sense the distance between the ultrasonic sensor and have those values sent through serial communications. To test the algorithm, grab a ruler and figure out what the resolution of the sensing system is as well as its precision. To test the resolution, move an object in front of the sensor very slightly to see what the minimal change detected by the sensor is. To test the precision, put an obstacle in front of the sensor and move it in millimeter increments. The resolution of the sensing system should be similar to the following:

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Schematic2_Measurement%20Locations.jpg" width="500">
  <br>
  <b>Schematic 2:</b> Measurement Locations
</p>


| Box Location Number | Distance From Sensor | Sensor Reading |
|---------------------|----------------------|----------------|
| 1                   | 1.5 cm               | 2.73 cm        |
| 2                   | 2.0 cm               | 2.08 cm        |
| 3                   | 3.0 cm               | 3.04 cm        |
| 4                   | 4.5 cm               | 4.41 cm        |
| 5                   | 6.5 cm               | 5.90 cm        |
| 6                   | 11.5 cm              | 11.18 cm       |
| 7                   | 16.5 cm              | 20–32 cm *     |

**Table 1: Location Change Readings**

*When the object is far enough away from the sensor, there is a lot of noise in the readings. This is to be expected because the sensors have a range of clear readings which location 7 surpasses. 

Note: At location 1, or the initial measurement, the object being used is as close as it can be to the sensor as possible. The 1.5 cm distance from sensor represents the object hitting the mounting plate (the red rectangle on the schematic). 

After moving the obstacle by a millimeter, the qualitative precision should be similar to the following:

Starting the box from touching the edge of the Sparkfun mounting plate, the box is 1.5 cm from sensor. The reading is 2.73 cm
Moving the box only 1 mm away from the sensor, the reading is still 2.37. 

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Fig4_Measuring%20Sensor.jpg" width="500">
  <br>
  <b>Figure 3:</b> Measuring Qualitative Precision
</p>

**Resulting code for Part 1**
<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Code1.jpg" width="500">
  <br>
  <b>Code 1:</b> Code for Distance Sensing
</p>

**Part 2- Move it**
To move on to the next part of the lab, do not disconnect the ultrasonic sensor from the Redboard. However, change the pin locations of the ultrasonic sensor to pins 7 and 6. Next, the motor driver and motors as shown below:

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Schematic2_motors%20hooked%20up.jpg" width="500">
  <br>
  <b>Schematic 3:</b> Motors hooked up to TB6612FNG and to Redboard
</p>

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Fig3_motors%20hooked%20up.jpg" width="500">
  <br>
  <b>Figure 4:</b> Circuit with Motors hooked up to the TB6612FNG and to Redboard
</p>

Once everything is connected, write a program to control the movement of both motors, using the code shown in the SparkFun Inventor's Kit Experiment Guide for guidance. Insert commands via the serial port to move both motors at three different speeds (slow, medium, fast) and document all code. Determine the minimum speed, which will be a number within the code, required for the motors to move forward. Test the program by making the motors turn right, turn left, and move backward at any speed. Finally, include the code from the distance sensor to make the motors stop when the distance measured is less than 10 cm, and demonstrate the code to the instructor.

**Resulting code for Part 2**
<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Code2part1.png" width="500">
  <br>
  <b>Code 2 Sheet 1:</b> Circuit with Motors hooked up to the TB6612FNG and to Redboard
</p>

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Code2part2.png" width="500">
  <br>
  <b>Code 2 Sheet 2:</b> Circuit with Motors hooked up to the TB6612FNG and to Redboard
</p>

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Code2part3.png" width="500">
  <br>
  <b>Code 2 Sheet 3:</b> Circuit with Motors hooked up to the TB6612FNG and to Redboard
</p>

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Code2part4.png" width="500">
  <br>
  <b>Code 2 Sheet 4:</b> Circuit with Motors hooked up to the TB6612FNG and to Redboard
</p>

<p align="center">
  <img src="https://github.com/faco229/Lab-6-Report/blob/main/Code2part5.png" width="500">
  <br>
  <b>Code 2 Sheet 5:</b> Circuit with Motors hooked up to the TB6612FNG and to Redboard
</p>

---

## Results
To find test the program, make the motors turn right, turn left, and go backward at any speed.
The results of this lab should be demonstrated to the instructor. In addition, the code used for Part 1 and Part 2 should be examined for approval by the instructor. The motors should stop when the distance of the object is less than 10 cm. 

---

## Discussion/Questions
**What is the minimum speed number for the motors to move forward?**

-The slowest the ‘Slow_speed’ can go is 80 rpm

---

## Conclusion
In this lab, we successfully demonstrated the integration of ultrasonic sensors and motor drivers to enable object detection and obstacle avoidance in a mobile robot. Through the experiments, we tested the precision and resolution of the ultrasonic sensor, confirming its ability to detect subtle changes in distance and identify limitations in sensor accuracy at greater distances. We also developed and tested code to relay distance data through serial communication and blended this feedback into a motion control system. This allowed the robot to interpret distance measurements and respond, stopping when an object was detected within 10 cm.

Additionally, we gained hands-on experience with the TB6612FNG motor driver and learned how to manipulate motor direction and speed through pulse width modulation (PWM). By programming various movement commands and establishing minimum speed thresholds, we were able to control the motion with precision. This lab not only reinforced foundational concepts in sensor technology and motor control but also illustrated the practical applications of these components in real-world robotics systems, such as collision prevention mechanisms in vehicles.



**Citations**

Copilot. (2025). Introduction to Ultrasonic Sensors and Actuators in Robotics. Retrieved from [Quinn’s with Copilot].

Copilot. (2025). Board Overview of TB6612FNG Breakout. Retrieved from [Quinn’s conversation with Copilot].

Copilot. (2025). Methods for Ultrasonic Sensor and Motor Driver Lab. Retrieved from [Quinn’s conversation with Copilot].

Copilot. (2025). Program for Controlling Motor Movement and Distance Sensing. Retrieved from [Quinn’s conversation with Copilot].

SparkFun. (2025). SparkFun Motor Driver - Dual TB6612FNG (with Headers). Retrieved from https://market.samm.com/sparkfun-motordriver-dual-tb6612fng-with-headers





---

*End of Lab Report*

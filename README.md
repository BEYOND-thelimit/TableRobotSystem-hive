# Table Robot System for fully automating restaurant service.
**Capston Design project at Hanyang University ERICA** \
This repository contains only the project description. The code implementation and usage guide can be found in the following repositories:
- **Multi-robots planning** on *our main PC(our laptop)*: [https://github.com/BEYOND-thelimit/hive_main](https://github.com/BEYOND-thelimit/hive_main)
- **Vision system** on *Jetson Orin*: [https://github.com/BEYOND-thelimit/hive_vision](https://github.com/BEYOND-thelimit/hive_vision)
- Each robot **controller** on *Raspberry Pi*: [https://github.com/BEYOND-thelimit/hive_robot](https://github.com/BEYOND-thelimit/hive_robot)
- Gazebo Simulation: [https://github.com/BEYOND-thelimit/hive_simulations](https://github.com/BEYOND-thelimit/hive_simulations)

### Team Members :
*Dahyun Kim, *Geunwoo Kwon, *Jeongmok Kim, *Jiyun Yang, *Seunghak Bae, *Taehun Ryu \
**Equal contribution (alphabet order)*

For more infromation, refers to the our [team introducement](https://github.com/BEYOND-thelimit).

### Advisor :
Prof. Wansoo Kim

---

## Abstract
Table Robot System aim at fully automating restaurant service. Utilizing ceiling-mounted cameras, the system enhances object detection and dynamic path planning algorithm, thus reducing labor costs and improving efficiency. Initial findings show significant increases in service speed and reductions in human server dependency, highlighting the system's potential to revolutionize restaurant operations.

## Workflow
The table robot system we propose allows a single robot to function as a table for one person, simultaneously performing serving and seating tasks. The process of our proposed system is as follows:

1. Guests arriving at the restaurant select the number of people and the seating location.
2. A robot suitable for the number of people moves to the selected location and forms a table.
3. Once the table formation is complete, additional robots handle the serving tasks.
4. After the guests leave, the robot that formed the table returns to its designated station.

Through this process, we have developed a table robot system that focuses on the complete automation of the restaurant hall and the maximization of space utilization.

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/90ac9c9b-c8e1-4ed7-a822-d9aaa23c3f5d">

## Hardware
> @Jeongmok Kim

We designed the mechanical structure as a mobile robot, similar to a one-person table in a restaurant, so that the tables can be combined with each other. Acrylic and aluminum profiles were used for the body, and pa6-cf was used for the bearing box and shaft.
A DC-CV converter was used because the motor's rated voltage to output torque to cover the desired payload was 24V, and the Raspberry PI 4b, a control board, and sensors including encoders and Lidar, were rated at 5V.
In addition, since the robot had to handle a light and large payload, it was selected as a lithium-ion battery with a high output compared to its weight, and the capacity was configured to be more than 8,000mAh to operate for up to 6 hours.

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/3f633c3a-b7cf-4f96-b05d-f7c102c1c04f">

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/c0878edc-6ca1-4d09-aa62-c0e6c2e57a2d">

## Grid map generation
> @Jiyun Yang

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/7461861d-5672-464f-a7b3-67d185864e6e">

## Localization and Robot Detection
> @Dahyun Kim: Robot Detection \
> @Taehun Ryu: EKF localization, coordinates integration

We utilize two sources of information to estimate the position of the robot. The first source is the data measured by sensors attached to the robot, and the second source is the information obtained from a camera located externally (on the ceiling). We perform EKF localization using the LiDAR, Encoder, and IMU sensors mounted on the robot. The camera employs YOLOv8 to determine the position of the robot.

We determine the final coordinates by performing linear interpolation using appropriate weights based on the two acquired sources of information.

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/569805f7-34b8-4c25-b772-32be5fc387ae">

## Control
> @Geunwoo Kwon \
> @Seunghak Bae

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/35c09973-aad1-4ce3-a345-247df3e847e4">

## System architecture
<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/acd450bb-b491-4a59-94d1-2160eff4696a">

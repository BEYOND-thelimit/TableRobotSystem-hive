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
<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/90ac9c9b-c8e1-4ed7-a822-d9aaa23c3f5d">

## Hardware
> @Jeongmok Kim

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/3f633c3a-b7cf-4f96-b05d-f7c102c1c04f">

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/c0878edc-6ca1-4d09-aa62-c0e6c2e57a2d">

## Grid map generation
> @Jiyun Yang

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/7461861d-5672-464f-a7b3-67d185864e6e">

## Localization and Robot Detection
> @Taehun Ryu: EKF localization, coordinates integration \
> @Dahyun Kim: Robot Detection

We utilize two sources of information to estimate the position of the robot. The first source is the data measured by sensors attached to the robot, and the second source is the information obtained from a camera located externally (on the ceiling). We perform EKF localization using the LiDAR, Encoder, and IMU sensors mounted on the robot. The camera employs YOLOv8 to determine the position of the robot.

We determine the final coordinates by performing linear interpolation using appropriate weights based on the two acquired sources of information.

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/569805f7-34b8-4c25-b772-32be5fc387ae">

## Control
> @Geunwoo Kwon \
> @Seunghak Bae

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/35c09973-aad1-4ce3-a345-247df3e847e4">

## System architecture
<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/acd450bb-b491-4a59-94d1-2160eff4696a">

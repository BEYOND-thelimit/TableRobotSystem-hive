# Table Robot System for fully automating restaurant service.

### It contains only the project description
The code implementation and usage guide can be found in the following repositories:
- Multi-robots planning: [@hive_main](https://github.com/BEYOND-thelimit/hive_main)
- Vision system: [@hive_vision](https://github.com/BEYOND-thelimit/hive_vision)
- Each robot controller: [@hive_robot](https://github.com/BEYOND-thelimit/hive_robot)
- Gazebo Simulation: [@hive_simulations](https://github.com/BEYOND-thelimit/hive_simulations)

### Team Members :
*Dahyun Kim, *Geunwoo Kwon, *Jeongmok Kim, *Jiyun Yang, *Seunghak Bae, *Taehun Ryu \
**Equal contribution (alphabet order)*

For more infromation, refers to the our [team introducement](https://github.com/BEYOND-thelimit).

### Advisor :
Prof. Wansoo Kim

### Workshop paper
양지윤, 권근우, 김다현, 김정목, 류태훈, 배승학, 김완수*.(2024).*"식당 홀의 완전 자동화를 위한 테이블 로봇 시스템"*. 제어로봇시스템학회 국내학술대회 논문집, 1135-1136.(**Undergraduate Students Paper Award**) [[DBpia](https://www.dbpia.co.kr/journal/articleDetail?nodeId=NODE11909262)]

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
In addition, since the robot had to handle a light but large payload, it was selected as a lithium-ion battery with a high output compared to its weight, and the capacity was configured to be more than 8,000mAh to operate for up to 6 hours.

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/3f633c3a-b7cf-4f96-b05d-f7c102c1c04f">

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/c0878edc-6ca1-4d09-aa62-c0e6c2e57a2d">

## Grid map generation
> @Jiyun Yang

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/7461861d-5672-464f-a7b3-67d185864e6e">

## Localization and Robot Detection
> @Dahyun Kim \
> @Taehun Ryu

We utilize two sources of information to estimate the location of the robots. The first source is the location measured by sensors attached to the robot. In this process, We perform EKF localization using the LiDAR, Encoder, and IMU sensors mounted on the robot. Also, the ICP algorithm is used to get odometry information from the LiDAR sensor. The second is obtained from a camera located externally (on the ceiling). It uses YOLOv8 for object detection and tracking.

The final coordinates are determined by performing linear interpolation using appropriate weights based on the two acquired sources of information. The weights are expressed as a function of the reliability of the estimated robot position in the camera.

The reason, why we use two pieces of information, is that the controller and the planner use different systems. The controller uses the world coordinate system, while the planner operates in the pixel coordinate system, so we needed an appropriate compromise.

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/569805f7-34b8-4c25-b772-32be5fc387ae">

## Control
> @Geunwoo Kwon \
> @Seunghak Bae

We used the D* Lite Algorithm for path planning in dynamic environments, and to achieve smooth driving through each point, we applied Bezier interpolation for smooth navigation.

<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/35c09973-aad1-4ce3-a345-247df3e847e4">

## System architecture
<img width="600" alt="image" src="https://github.com/BEYOND-thelimit/TableRobotSystem-hive/assets/73813854/acd450bb-b491-4a59-94d1-2160eff4696a">

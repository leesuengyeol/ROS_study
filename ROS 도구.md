**ROS 도구**



**1. RViz(ROS Visualization Tool)**

-센서 및 로봇 관련 데이터 시각화가 매우 간단

- ROS의 3D 시각화 툴

- 다양한 센서의 값을 시각화

- URDF : 로봇 외형의 표시와 계획된 동작을 표현

- Navigation
- manipulation
- simulation
- 원격 제어



**2. RQT**

-ROS 의 종합 GUI Tool



- rqt_image_view

  raspicam  사용 - <http://emanual.robotis.com/docs/en/platform/turtlebot3/appendix_raspi_cam/>

  -roslaunch raspicam_node camerav2_1280x960.launch

  -rostopic list

  -rostopic echo /노드이름    => message 전달 내용

  -rostopic info /노드이름 => msg type

- rqt_graph     

  -현재 노드들의 상태를 확인  rqt_plot

- -여러가지 값들을 시간축으로하여 plot으로 표현

- rqt_bag

  -rqt를 녹화후 다시 실행 가능

  -rosbag record /topic 이름  =>녹화

  -rqt_bag => 재생



**3. Gazebo**

-로봇 개발에 필요한 3차원 시뮬레이션을 위한 로봇, 센서 ,환경 모델등을 지워나고 물리 엔진을 탑재하여 실제와 근사한 결과를 얻을 수 있는 3차원 시뮬레이터


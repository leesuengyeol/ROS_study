**ROS Programming**



**표준 단위**

![image](https://user-images.githubusercontent.com/48343629/57896877-e76e5400-788d-11e9-8694-45541bf39f7c.png)



​     

**roscore**

master 로써의 역할

rosout -> log 기록

parameter server -> 노드가 parameter server 를 참조하여 행동을 변화





**Topic / Publisher / Subscriber**
**1. 패키지 생성**

​										패키지이름		/ 의존성

catkin_create_pkg ros_tutorials_topic message_generation std_msgs roscpp

만들어진 파일

include	 			-> 헤더 파일 폴더

src			 			-> 소스 코드 폴더

CMakeLists.txt	-> 빌드 설정 파일

package.xml		-> 패키지 설정 파일



**2. 패키지 설정 파일(package.xml)**

xml 형식 -  <자료형>  내용 </자료형>

참고 <http://mm.sookmyung.ac.kr/~sblim/lec/xml-PBL/xml10-2xml.htm>

**자료형**

version - 현재 버전

description -설명

Author - 저자

maintainer - 다른사람이 지속적으로 개발을 하기위해 가장 최근 수정한 저자

URL 

1) bugtracker 	사용자와 커뮤니케이션하기위해

2) repository	  저장소	

3)  website 		문서 (보통 robotis site)



build tool_depend - build 할때 어떤걸 쓰는가?  ex) catkin

build_depend	 	- build 할때 의존성

run_depend 			-실행 할때 의존성 	



**3. 빌드 설정 파일 (CMakeLists.txt)**

주요  메소드

**cmake_minimum_required(VERSION 2.8.3)**

-cmake의 최소 요구 버전

-**CMake  (Cross Platform Make) 란?**

멀티 플랫폼으로 사용할 수 있는 make의 대용품을 만들기 위한 오픈소스 프로젝트이다

스스로 기존의 Make의 과정을 수행하지는 않고 **지정된 운영체제에 맞는 Make파일의 생성**만을 수행한다 **Meta Make** 라고도 불린다



**project(my_first_ros_pkg)**

-패키지의 이름, package.xml에서 입력한 패키지 이름을 그대로 입력해 줘야만 에러가 발생하지 않는다!



**find_package(catkin REQUIRED COMPONENTS message_generation std_msgs roscpp) **

-catkin 빌드를 할때 요구되는 구성 요소 패키지, **의존성 패키지들을 적어준다**

-**사용자가 만든 패키지가 의존하는 다른 패키지를 먼저 설치하게 만드는 옵션**

-여기에 입력된 패키지가 없다면 캐킨 빌드할 때 사용자에게 에러가 표시된다. 



**find_package(Boost REQUIRED COMPONENTS system)**

-ROS 이외의 패키지를 사용할때 사용되는 방법

-위의 find_package 와 같다



**catkin_python_setup()**

-rospy를 사용할 때 설정하는 옵션

-파이썬 설치 프로세스인 setup.py를 부르는 역할



**add_message_files(FILES MsgTutorial.msg)**

-메시지 파일을 추가하는 옵션

-**FILES를 사용하면 현재 패키지 폴더의 msg폴더 안의 .msg 파일들을 참조하여 헤더 파일 (*.h)를 자동으로 생성하게 된다**



**add_service_files(FILES Service1.srv Service2.srv)**

-사용하는 서비스 파일을 추가하는 옵션

-**FILES 를 사용하면 패키지 폴더의 srv 폴더 안의 .srv 파일들을 참조**



**generate_message(DEPENDENCIES std_msgs)**

-의존하는 메시지를 설정하는 옵션

-**DEPENDENCIES 옵션에 의해 std_msgs 메시지 패키지를 사용**



**generate_dynamic_reconfigure_options(cfg/DynReconf1.cfg cfg/DynReconf2.cfg)**

-dynamic_reconfigure 을 사용할 때 참조하는 설정 파일을 불러오는 설정



**catkin_package(**

**INCLUDE_DIRS include **

**LIBRARIES ros_tutorials_topic**

**CATKIN_DEPENDS roscpp std_msgs**

**DEPENDS system_lib**

**)**

-catkin 빌드 옵션

-**INCLUDE_DIRS** :  뒤에 설정한 패키지 내부 폴더인 include의 헤더파일을 사용하는 설정

-**LIBRARIES** : 뒤에 설정한 패키지의 라이브러리를 사용하겠다는 설정

-**CATKIN_DEPENDS** : roscpp나 std_msgs 등 의존하는 패키지를 지정

-**DEPENDS** : 시스템 의존 패키지를 기술하는 설정



**include_directories**(

${catkin_INCLUDE_DIRS}

)

-인클루드 폴더를 지정할 수 있는 옵션

-${catkin_INCLUDE_DIRS}는 각 패키지안의 include 폴더를 의미하고 이 안의 헤더 파일을 이용하겠다는 설정



**add_library(**

**my_first_ros_pkg **

**src/${PROJECT_NAME}/my_first_ros_pkg.cpp**

**)**

-빌드 후 생성할 라이브러리를 선언

-src/${PROJECT_NAME}/my_first_ros_pkg.cpp 를 참조하여 my_first_ros_pkg 라이브러리를 생성하는 명령



**add_dependencies(**

**my_first_ros_pkg **

**${$PROJECT_NAME}_EXPORTED_TARGETS} **

**${catkin_EXPORTED_TARGETS} **

**)**

 -해당 라이브러리 및 실행파일을 빌드하기에 앞서 생성해야 할 의존성이 있는 메시지 및 dynamic reconfigure 가 있으면 이를 우선적으로 수행하라는 설정

**dynamic reconfigure:  어떤 로봇의 이동 속도나 센서 설정등을 변경 해주는 패키지**



**add_executable(my_first_ros_pkg_node src/my_first_ros_pkg_node.cpp)**

-빌드 후 생성할 실행 파일에 대한 옵션을 지정한다

-src/my_first_ros_pkg_node.cpp 을 참조하여 

my_first_ros_pkg_node 실행 파일을 생성하라는 내용이다.

-생성할 파일이 2개 이상인 경우 add-executable 항목을 추가로 적어준다.



**target_link_libraries(my_first_ros_pkg_node ${catkin_LIBRARIES})**

-지정 실행 파일을 생성하기 앞서 링크해야 하는 라이브러리와 실행 파일을 링크해주는 옵션



**4. 메시지 파일 작성**

-어떤 형식의 메시지를 주고 받을지 정의하는 파일

패키지에서 안에서

mkdir msg 

cd msg

vim 'Msg name' 만들기



**5. 퍼블리셔 노드 만들기**

![image](https://user-images.githubusercontent.com/48343629/57896906-0371f580-788e-11e9-866e-6d01003b3d54.png)
![image](https://user-images.githubusercontent.com/48343629/57896927-18e71f80-788e-11e9-85b6-d05b9e510803.png)


![image](https://user-images.githubusercontent.com/48343629/57896948-2d2b1c80-788e-11e9-878b-cc86b92010d0.png)




**6. 서브스크라이버 노드 작성**

![image](https://user-images.githubusercontent.com/48343629/57896961-3d42fc00-788e-11e9-91d0-b255966fe99d.png)

![image](https://user-images.githubusercontent.com/48343629/57896968-4764fa80-788e-11e9-8933-6e1ceba88321.png)




 **7. ROS 노드 빌드**

cd ~/catkin_ws -> catkin 폴더로 이동

catkin_make 	-> catkin 빌드 실행

**파일 시스템**

/build 폴더에는 catkin 비륻에서 사용된 설정 내용이 저장

/deve/lib/ros_tutorials_topic 폴더에는 실행 파일이 저장

/devel/include/ros_tutorials_topic 폴더에는 메시지 파일로부터 자동 생성된 메시지 헤더 파일이 저장




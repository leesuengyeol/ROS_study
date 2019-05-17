ROS 용어



**1. 노드와 패키지**



Node

-최소 단위의 실행 가능한 프로세서 (ROS의 최소한의 실행단위)

-각 노드는 메시지 통신으로 데이터를 주고 받음



Publisher node 

-메시지를 보내는 노드



Subscriber node

-메시지를 받는 노드



Package

-하나 이상의 노드, 노드 실행을 위하 정보 등을 묶어 놓은 것

=> metapackage : package의 묶음





**2.통신**



**Message**

-노드간의 데이터를 주고받음

-integer , floating point , boolean 과 같은 변수 형태이다





**Topic**

 -단방향 , 연속성을 가진 메시지 통신 방법

-1대1 뿐만 아니라 1:N , N:1 , N:N 통신 가능



![](C:\ROS\사진\다운로드.png)



Publisher node 

-메시지를 보내는 노드



Subscriber node

-메시지를 받는 노드



**Service**

-양방향 , 1회성을 가진 메시지 통신 방법

![](C:\ROS\사진\다운로드 (1).png)



Service server: 요청 , Service client: 응답



**Action**

-service 와 비슷하지만 중간결과에대한 action feedback 을 보내며 복잡한 task에서 주로 사용됨

![](C:\ROS\사진\다운로드 (2).png)

Action server: 요청 , Action client: 응답





**3.기타**

**네임(Names)**

-노드, 메시지(topic, service ,action)의 고유 식별자

노드, 메시지 이름 변경시 사용


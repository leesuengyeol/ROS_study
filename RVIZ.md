**RVIZ**

rviz 는 tf 변환 시스템을 사용한다

이것은 데이터를 조직화한 프레임으로 변환시켜주며 전체 참조 프레임이 된다



두가지 프레임이 존재하는데 fixed frame과  target frame이 있다



fixed frame

fixed 프레임은 참조 프레임으로 사용되는데 "world"프레임을 의미한다 (맵이라는 의미 같다)



target frame

타겟프레임은 화면을 위한 것이다 만약 타겟프레임이 맵이라면 로봇이 맵주면을 움직이는게 보이겠지만 만약 타겟 프레임이 로봇이 밑면(base of robot)이라면 로봇은 다른 모든 것들이 상대적으로 움직이는 동안 같은 장소에 머무를것이다



tf 변환

tf는 사용자가 시간에 따라 여러 좌표 프레임을 추적할 수 있도록 해주는 패키지. tf는 시간에 버퍼링된 트리 구조에서 좌표 프레임 간의 관계를 유지하고 사용자가 원하는 시점에 임의의 두 좌표 프레임 간에 점, 벡터 등을 변환할 수 있도록 한다.



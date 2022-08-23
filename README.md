# yolo
Yolo simple tutorial

## darknet_ros
yolo는 심층신경망을 이용한 객체 탐지 딥러닝 모델입니다. 물체의 정보를 실시간으로 탐지하며, 이를 rostopic 으로 받기 위해서는 `darknet_ros` repository를 사용하여야 합니다.

## Installation
`darknet_ros` 의 오픈소스 깃허브 레포지토리는 [여기](https://github.com/leggedrobotics/darknet_ros/tree/master)입니다.\
한글 참고문헌은 [여기](https://velog.io/@qaszx1004/darknetrosYolo-v3-tiny)입니다.

먼저 자신의 워크스페이스에 들어가서, `darknet_ros`를 클론합니다. 
```
cd catkin_workspace/src
git clone --recursive git@github.com:leggedrobotics/darknet_ros.git
cd ../
```
자신의 워크스페이스에서 빌드해줍니다. 기능을 충분히 사용하려면 Release 모드로 빌드해 주어야 합니다.
```
catkin_make -DCMAKE_BUILD_TYPE=Release
```
catkin_make를 진행할 때, gcc version은 6이하여야 합니다. 컴파일 과정에서 오류가 나오면 gcc version을 체크해보시고, 버전이 6보다 높다면, [여기](https://blog.naver.com/tinz6461/222181958151)를 참고해 버전을 변경해주세요.
```
gcc --version
```

패키지를 등록을 최신화합니다.
```
rospack profile
source devel/setup.bash
```
## Image topic
darknet_ros 에 기본으로 설정된 Image topic명을 변경해 주어야 합니다. 이번 튜토리얼에서 사용할 로스벡의 이미지 토픽명은 `/usb_cam/image_raw`이므로, 이것으로 변경해 줍니다.
```
gedit ~/catkin_workspace/src/darknet_ros/darknet_ros/config/ros.yaml
```
camera reading 의 topic 을 `/usb_cam/image_raw`로 변경해줍니다.

## Launch darknet_ros
darknet_ros를 launch 해줍니다.
```
roslaunch darknet_ros darknet_ros.launch 
```
image topic을 받기위해 차량 주행 토픽을 받습니다.
```
rosbag play new_camera_whole.bag
```





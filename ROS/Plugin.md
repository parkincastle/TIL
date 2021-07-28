# Plugin이란?
Gazebo 플로그인은 URDF 모델에 더 많은 기능을 제공하고 센서 출력 및 모터 입력에 대한 ROS 메시지 및 서비스 호출을 연결할 수 있다. 

<br>

## 플러그인 유형
1. Physical Model API에 대한 액세스를 제공하기 위한 ModelPlugins
2. Sensor API에 대한 액세스를 제공하기 위한 SensorPlugins
3. Rendering Visual API 에 대한 액세스를 제공하기 위한 VisualPlugins

<br>

## `Model Plugin`을 추가하는섹스
즉 ModelPlugin, `robot` 요소 내무의 URDF에 삽입된다. 그리고 Gazebo에 전달된 정보를 나타내기 위해 <gazebo>태그를 사용한다.

<br>

```JavaScript
<robot>
  ... robot description ...
  <gazebo>
    <plugin name="differential_drive_controller" filename="libdiffdrive_plugin.so">
      ... plugin parameters ...
    </plugin>
  </gazebo>
  ... robot description ...
</robot>
```

<br>

Gazebo내 에서 로봇 모델을 로드하면 `diffdrive_plugin` 코드에 모델 자체에 대한 참조가 제공되어 모델을 조작 할 수 있게 된다. 그리도 전달된 플로그인 매개변수를 읽기 위해 다체 SDF요소에 대한 참도를 제공한다.

<br><br>

## `Sensor Plugin`을 추가 하는 방법

센서 플러그인을 지정하는 것은 약간 다르다. Gazebo의 센서는 링크 





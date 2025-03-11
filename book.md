# Hi6 Robot Controller Operation Manual - Additional axes

{% hint style="warning" %}
The information presented in this manual is the property of Hyundai Robotics.

The manual may neither be copied, in part or in full, nor redistributed without prior written consent from Hyundai Robotics.

It may neither be provided to any third party nor used for any other purposes.

Hyundai Robotics reserves the right to modify this document without prior notification.

**Copyright ⓒ 2022 by Hyundai Robotics**
{% endhint %}
# 1. Introduction

This section explains the setup for additional axes except the basic robot axes.

</br>

## **【 Registration Procedure 】**

* Preparation Work  </br>
(1) Prepare the main unit (robot + additional axes) and wire harness  </br>
(2) Prepare the controller, one set of BD640 (required when applying additional axes of three or more), additional axis AMP, and signal cables  </br>
(3) Additional Axis Parameter  </br>
    Prepare the input data for the additional axis, including axis specifications, configuration, reduction ratio, motor, and AMP, in the format required for additional axis setting (refer to Section 3.2).  </br>
(4) Additional Axis Acceleration/Deceleration Time  </br>
Prepare the data needed to input the command acceleration/deceleration time for the additional axis (refer to Section 3.2). </br>

* Registration of Robot Type and Additional Axis Parameter  </br>
After connecting the wire harness between the main unit and the controller, initialize the system, select the robot type, enter the number of additonal axes, and then input the additional axis parameters (Maximum controllable axes: 16, including the robot)  </br>
※ If the robot type and additional axis parameters have already been registered before shipment, this process can be skipped.  </br>

* Connection and Inspection  </br>
Turn off the controller → Connect the necessary wires between the main unit and the controller → Turn on the controller → Set encoder calibration and the reference position (axis parameters) for the servo system.  </br>

* Completion  </br>
After configuring the additional axis operating environment, save the hi6_proj.json file to an external storage device (USB memory).
# 2. Presetting

* 접속할 부품 및 자재들을 확인합니다.
* 미리 계산해 둔 데이터나 선정된 부가축 정보 등이 준비되었는지 확인합니다.
(감속비, AMP 사양, Motot 사양, 최고속, 가속시간 등)
* 축수에 따른 BD640와 AMP의 조합은 다음과 같습니다.

  | 축 구성 | BD/AMP 구성 |
  | :------------------: | :-------------------: |
    | 1축 \~ 6축</br>(기본6축) | BD640 1개</br>6축 AMP 1개 |
  | 7축 \~ 8축</br>(기본6축 + 부가2축) | BD640 1개</br>6축 AMP 1개</br>1축 AMP 1~2개 |
  | 9축 ~ 12축</br>(기본6축 + 부가6축) | BD640 2개</br>6축 AMP 2개 |
  | 13축 ~ 16축</br>(기본6축 + 부가12축) | BD640 2개</br>6축 AMP 2개</br>1축 AMP 1~4개 |

</br>

* 축수에 따라서 인터페이스 보드(BD6H0)의 딥스위치 설정이 필요합니다.

  <div align="left">

  | 명칭 | 용도 | 설정방법|
  | :------------------: | :-------------------: | :-------------------: |
  | SW1 | SSM1(BD640 1번 보드) 연결 시, 설정하는 스위치 | SSM1 연결 시: 1/2/3/4 스위치 OFF </br> 사용하지 않을 시: 1/2/3/4 스위치 ON |
  | SW2 | SSM1(BD640 2번 보드) 연결 시, 설정하는 스위치 | SSM2 연결 시: 1/2/3/4 스위치 OFF </br> 사용하지 않을 시: 1/2/3/4 스위치 ON |
  | SW3 | SSM1(BD640 3번 보드) 연결 시, 설정하는 스위치 | SSM3 연결 시: 1/2/3/4 스위치 OFF </br> 사용하지 않을 시: 1/2/3/4 스위치 ON |
  | SW4 | SSM1(BD640 4번 보드) 연결 시, 설정하는 스위치 | SSM4 연결 시: 1/2/3/4 스위치 OFF </br> 사용하지 않을 시: 1/2/3/4 스위치 ON |

  </div>

{% hint style="info" %}
 BD640 1 대당 8축 제어 가능, AMP 2종 (6축용, 1축용)
{% endhint %}
# 3. Setup for Robot Type and Additional Axis parameter
## 3.1 Setting up Robot Type and Number of Additional Axes

다음과 같은 순서로 부가축을 설정합니다.

(1) 수동모드의 『시스템』 → 『5: 초기화』 → 『2: 로봇타입선택』 메뉴에서 사용하고자 하는 로봇타입을 선택합니다.

<p align="center">
 <img src="../../_assets/robottype.PNG" width="70%"></img>
 <em><p align="center">그림 3.1 로봇 타입 선택 화면</p></em>
</p>

</br>

{% hint style="info" %}
 로봇타입 및 부가축 정수를 설정하기 위해서는 엔지니어코드(R314)가 입력된 상태에서만 가능합니다. 모니터 화면 상단 우측의 “e” 표시가 엔지니어 코드가 입력된 상태임을 보여줍니다.
{% endhint %}

</br>

(2) 부가축수를 입력하고 『확인』키를 눌러서 제어기를 재부팅합니다.

<p align="center">
 <img src="../../_assets/reboot.PNG" width="70%"></img>
 <em><p align="center">그림 3.2 제어기 재부팅 안내</p></em>
</p>

</br>

(3) 『시스템』 → 『5: 초기화』 → 『[5: 부가축 파라미터 설정](../2-parameters/parameters.md)』 메뉴로 진입합니다.

<p align="center">
 <img src="../../_assets/addaxes_menu.PNG" width="70%"></img>
 <em><p align="center">그림 3.3 부가축 파라미터 설정 메뉴</p></em>
</p>
## 3.2 부가축 정수 설정


(1)	아래와 같은 『부가축 정수 설정』화면을 확인합니다.


<p align="center">
 <img src="../../_assets/addaxes.PNG" width="70%"></img>
 <em><p align="center">그림 3.4 부가축 파라미터 설정</p></em>
</p>


(2)	부가축 정수를 설정합니다.  
(3)	입력 종료는 『OK』키를 누릅니다. 


<br/>

---

**【부가축 정수】**

(1)	축 사양 : 부가축 종류를 <베이스, 서보건, 포지셔너, 지그, 실러> 중에서 선택합니다.  
부가축 사양을 결정할때는 논리적인 부가축 순서에 따라 베이스 → 서보건 → 포지셔너 → 지그 → 실러 순을 지켜야합니다.  

(2)	축 구성 : 축의 동작형태와 방향을 선택합니다.  
직동 베이스축(주행축)인 경우는 전/후축 주행이면 X, 좌/우축 주행이면 Y로, 상/하축 주행이면 Z로 선택합니다. <br>
베이스축이 로봇 좌표계와 동일한 방향으로 설치되지 않은 경우는 <임의>로 선택하고 『베이스축 캘리브레이션』을 실행합니다. <br>
회전 베이스축도 직동 베이스축과 같이 Rx/Ry/Rz를 선택하거나 <임의>로 선택하여 『베이스축 캘리브레이션』을 실행합니다. <br>
축 사양을 <지그>나 <실러>로 선택한 경우에는 제어모드를 <위치제어>나 <속도제어>중에서 선택할 수 있으며 속도제어인 경우는 모터속도 지령에 따라 모터가 회전합니다.<br>  
서보건을 설정하는 경우는 『[스폿용접 기능설명서](https://hrbook-hrc.web.app/#/view/doc-spot-weld/korean/2-servo-gun-initial-setting/README)』, 포지셔너를 사용하는 경우는 『[포지셔너동기 기능설명서](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/korean/README)』를 참조하십시오.

(3)	축 위치 : 부가축의 물리적인 구성을 사용자가 지정하여 사용할수 있도록 합니다.

<center>

|축위치 정보 |설정값 |
|:---:|:---:|
| BD : '1'  | BD640보드 번호 : 1~2  |
| Axis : '7' | BD640 #1 : 7~8 </br>BD640 #2 : 1~8  |

  ※ '1', '7' 로 설정하였다면, BD640 1번의 7번째 축으로 설정됨  
</center>

(4) 감속비 : 모터 회전수당 축의 이동량을 등록합니다.  
직동축은 모터 회전수당 축 이동거리를 mm로, 회전축은 모터 회전수당 축 회전각도를 deg로 등록합니다. <br>
부호는 모터의 정방향(엔코더가 증가하는 방향)이 축 동작방향과 일치하여 부가축 좌표치가 증가하면 “+”이고, 반대로 좌표치가 감소한다면 “-“로 정합니다. <br>
아래 예시를 참고하십시오.  

- 예 1) 1/100감속기만 사용하는 회전축이라면,  
모터 100회전에 축이 360deg회전하므로,  
감속비 = + 360 / 100 [deg/rev]  
- 예 2) 1/20감속기와 PCD 110mm인 랙피니언을 사용하는 직동축이라면,  
모터 20회전에 110xPhi(=3.14159)=345.5749[mm]를 이동하므로,  
감속비 = + 3455749 /200000 [mm/rev]  
- 예 3) 1/5 감속기와 Lead 5mm인 볼스크류를 사용하는 직동축이라면,  
모터 5회전에 축이 5mm이동하므로,  
감속비 = + 5 / 5 [mm/rev]  

(5)	소프트리밋 : 로봇 유효동작영역(부가축 소프트 리미트)을 설정합니다. <br>
직동축은 [mm]로 회전축은 [deg]로 설정하며 『시스템』 → 『3: 로봇 파라미터』 → 『3: 소프트웨어 리미트』에 설정값이 반영됩니다.  

(6)	AMP 사양 : 부가축에 사용할 AMP의 사양을 선택합니다.  
IPM 기호를 선택하고 Hall Sensor 사양을 숫자 0-9 로 입력하여 AMP 사양을 선택합니다. AMP의 형식 사양은 다음과 같습니다.  


<p align="center">
 <img src="../../_assets/amp.PNG" width="60%"></img>
 <em><p align="center">그림 3.5 IPM 사양</p></em>
</p>

IPM 기호와 Hall Sensor 기호에 따라 아래의 정격 용량을 갖습니다.  


<p align="center">
 <img src="../../_assets/ipm_hall.PNG" width="60%"></img>
 <em><p align="center">그림 3.6 Hall sensor 사양</p></em>
</p>

(7)	Motor 사양 : 부가축에 사용되는 모터 사양을 선택합니다.  
모터의 용량을 먼저 선택하고, 모터 사양을 선택합니다.  
모터의 세부 속성값 중 일부에서 사소한 변경이 있는 경우, 동일한 모터 형번에 rev 번호가 추가되는 경우가 있습니다. <br>
이 경우 rev 번호가 가장 높은 최신 모터정보를 선택 하시기를 권장 합니다. </br>
Ex> TSM3563N7020E731, TSM3563N7020E731_R1, TSM3563N7020E731_R2 중 TSM3563N7020E731_R2 모터를 선택 

(8)	가감속 파라미터 : 부가축의 최고속과 가속시간을 설정합니다.  
여기서 설정한 값은 『시스템』 → 『3: 로봇 파라미터』 → 『34: 가감속 파라미터』에 설정하는 것과 동일하게 적용됩니다. <br>
부가축의 최고속을 사용자가 지정하지만, 모터 정격속도에 따라 제한됩니다. <br>
부가축 동작중 진동이 발생하면 가속시간을 조정해야 합니다.  
## 3.3 메카니즘 설정

(1)	메커니즘 설정  
『시스템』 → 『5: 초기화』 → 『6: 메커니즘 설정』을 선택합니다.  

<p align="center">
 <img src="../../_assets/mechanism.PNG" width="70%"></img>
 <em><p align="center">그림 3.7 메커니즘 설정</p></em>
</p>


부가축은 수동 조작시 메커니즘 그룹에 따라 조그키를 할당하기 위해 메커니즘 그룹을 설정해야 합니다. 로봇축은 메커니즘 M0으로 고정되어 있으며, 부가축은 메커니즘 M1~M7로 분류하여 선택합니다.  


<br/>

(2)	정수 파일 백업  
부가축 설정이 완료되고 나면 『서비스』 → 『5: 파일관리』에서 USB memory에 프로젝트 파일(hi6_proj.json)을 복사합니다.  

<p align="center">
 <img src="../../_assets/project.PNG" width="70%"></img>
 <em><p align="center">그림 3.8 설정 파일 백업</p></em>
</p># 4. Teaching & Run## 4.1 Manual Mode (Jog)


(1)	T/P상의 [메커니즘]키를 누르면 T/P상단의 상태표시창의 메커니즘 상태가 [1]로 표시되면서 메커니즘 그룹 1번에 대한 수동 조작이 가능해집니다.

(2)	부가축 수동조작은 좌표계에 관계없이 개별축 동작을 합니다. 다만, 주행축 은 좌표계 선택에 따라 다음과 같이 동작합니다.  
- 축 : 주행축 개별동작(설정된 축 방향으로 이동)  
- 직교, 툴 : 로봇 툴끝(TCP) 위치 및 자세고정 주행축 이동 동작 수행

(3)	수동동작 속도( S8기준 ) : 부가축 최고속의 25% (단, 직선최고속 250mm/sec로 제한)  


<br>
<br>
<br>

### 참고사항
부가축의 경우 사용자의 필요에 따라 임의로 장착 되는 제어축이기 때문에 일부 표준품을 제외하면 사전에 튜닝이 되어있지 않습니다.<br>
부가축의 제어 성능에 문제가 있는 경우 게인 튜닝이 필요합니다. </br>
[부가축 자동튜닝](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/korean-tp630/7-system/7-auto-calibration/7-Addaxis-autotuning)
# 4.2 Run

(1)	보간 Off
각축별 목표점 동시 도달 합니다.

(2)	직선보간
로봇 툴끝(TCP)이 직선보간(궤적,자세유지) 동작이 이루어 집니다. <br>
베이스축은 로봇과 연동하여 움직이면서 툴끝이 직선보간을 이루도록합니다. <br>
그 이외의 부가축은 로봇 툴끝과 관련이 없으나 목표점에 동시 도달합니다. <br>

(3)	원호보간
로봇 툴끝(TCP)이 직선보간(궤적,자세유지) 동작이 이루어 집니다. <br>
베이스축은 로봇과 연동하여 움직이면서 툴끝이 직선보간을 이루도록합니다. <br>
그 이외의 부가축은 로봇 툴끝과 관련이 없으나 목표점에 동시 도달합니다. <br>

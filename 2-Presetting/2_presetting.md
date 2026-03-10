# 2. Presetting

* Check the components and materials to be connected.
* Ensure that the pre-calculated data and selected additional axis information are prepared.
(Reduction ratio, AMP specifications, motor specifications, maximum speed, acceleration time, etc.)
* The combination of Servo board and AMP according to the number of additional axes is as follows.

  | Axis Configuration | BD/AMP Configuration |
  | :------------------: | :-------------------: |
    | 1 to 6 axes</br>(basically 6 axes) | 1 Servo board</br>1 AMP(6-axis type) |
  | 7 to 8 axes</br>(basically 6 axes + 2 additional axes) | 1 Servo board</br>1 AMP(6-axis type)</br>1 to 2 AMPs(1-axis type) |
  | 9 to 12 axes</br>(basically 6 axes + 6 additional axes) | 2 Servo boards</br> 2 AMP(6-axis type) |
  | 13 to 16 axes</br>(basically 6 axes + 12 additional axes) | 2 Servo boards</br>2 AMP(6-axis type)</br>1 to 4 AMPs(1-axis type) |

{% hint style="info" %}
 The servo boards for each controller are as follows:<br>
 (Hi6 : BD640, Hi7 : BD642)
{% endhint %}  

</br>

* DIP switch settings for interface board (BD6H0) Based on the number of additional axes.(※ Hi6 only)
  <div align="left">

  | Name | Purpose | Setting|
  | :------------------: | :-------------------: | :-------------------: |
  | SW1 | Switch for configuring SSM1 (BD640 Board 1) | When SSM1 is connected: Switches 1/2/3/4 OFF </br> When SSM1 is disconnected: Switches 1/2/3/4 ON |
  | SW2 | Switch for configuring SSM2 (BD640 Board 2) | When SSM2 is connected: Switches 1/2/3/4 OFF </br> When SSM2 is disconnected: Switches 1/2/3/4 ON |
  | SW3 | Switch for configuring SSM3 (BD640 Board 3) | When SSM3 is connected: Switches 1/2/3/4 OFF </br> When SSM3 is disconnected: Switches 1/2/3/4 ON |
  | SW4 | Switch for configuring SSM4 (BD640 Board 4) | When SSM4 is connected: Switches 1/2/3/4 OFF </br> When SSM4 is disconnected: Switches 1/2/3/4 ON |

<p align="center">
  <img src="../_assets/2_1_dip_switch_example.jpg" width="500">
  <em><p align="center">Figure 2.1 DIP switch example (SSM1 connected)</p></em>
</p>
  </div>

{% hint style="info" %}
Each Servo board can control up to 8 axes, with two types of AMPs available (6-axis type and 1-axis type).

{% endhint %}

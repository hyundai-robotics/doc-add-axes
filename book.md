
[__SOURCE](README.md)
# ${cont_model} Controller Operation Manual - Additional axes

[__SOURCE](0-about-this-manual/precautions.md)
# Precautions

{% include url="https://hrcontentsrelay-bmgae5hdbzapc4bc.koreacentral-01.azurewebsites.net/api/proxy?path=doc-common-pages/en/precautions.md" %}

[__SOURCE](1-Introduction/1_introduction.md)
# 1. Introduction

This section explains the setup for additional axes except the basic robot axes.

</br>

### **[ Registration Procedure ]**

* Preparation Work  </br>
(1) Prepare the main unit (robot + additional axes) and wire harness  </br>
(2) Prepare the controller, one set of BD640 (required when applying additional axes of three or more), additional axis AMP, and signal cables  </br>
(3) Additional Axis Parameter  </br>
    Prepare the input data for the additional axis, including axis specifications, configuration, reduction ratio, motor, and AMP, in the format required for additional axis setting (refer to Section 3.2).  </br>
(4) Additional Axis Acceleration/Deceleration Time  </br>
Prepare the data needed to input the command acceleration/deceleration time for the additional axis (refer to Section 3.2). </br>

* Registration of Robot Type and Additional Axis Parameter  </br>
After connecting the wire harness between the main unit and the controller, initialize the system, select the robot type, enter the number of additional axes, and then input the additional axis parameters (Maximum controllable axes: 16, including the robot)  </br>
* If the robot type and additional axis parameters have already been registered before shipment, this process can be skipped.  </br>

* Connection and Inspection  </br>
Turn off the controller → Connect the necessary wires between the main unit and the controller → Turn on the controller → Set encoder calibration and the reference position (axis parameters) for the servo system.  </br>

* Completion  </br>
After configuring the additional axis operating environment, save the hi6_proj.json file to an external storage device (USB memory).

[__SOURCE](2-Presetting/2_presetting.md)
# 2. Presetting

* Check the components and materials to be connected.
* Ensure that the pre-calculated data and selected additional axis information are prepared.
(Reduction ratio, AMP specifications, motor specifications, maximum speed, acceleration time, etc.)
* The combination of BD640 and AMP according to the number of additional axes is as follows.

  | Axis Configuration | BD/AMP Configuration |
  | :------------------: | :-------------------: |
    | 1 to 6 axes</br>(basically 6 axes) | 1 BD640</br>1 AMP(6-axis type) |
  | 7 to 8 axes</br>(basically 6 axes + 2 additional axes) | 1 BD640</br>1 AMP(6-axis type)</br>1 to 2 AMPs(1-axis type) |
  | 9 to 12 axes</br>(basically 6 axes + 6 additional axes) | 2 BD640</br> 2 AMP(6-axis type) |
  | 13 to 16 axes</br>(basically 6 axes + 12 additional axes) | 2 BD640</br>2 AMP(6-axis type)</br>1 to 4 AMPs(1-axis type) |

</br>

* DIP switch settings for interface board (BD6H0) Based on the number of additional axes.
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
Each BD640 can control up to 8 axes, with two types of AMPs available (6-axis type and 1-axis type).

{% endhint %}

[__SOURCE](3-Setup/3_setup.md)
# 3. Setup for Robot Type and Additional Axis parameter

[__SOURCE](3-Setup/1-robottype/robottype.md)
## 3.1 Setting up Robot Type and Number of Additional Axes

The additional axis is set up in the following order:

(1) Navigate to [System] → [5: Initialization] → [2: Robot type selection] and select the robot type.

{% hint style="info" %}
To configure the robot type and additional axis parameter setting, the engineer code (R314) must be entered. The "e" indicator at the top right of the monitor screen confirms that the engineer code has been entered.
{% endhint %}

(2) Enter the number of additional axes and press "OK" and reboot the controller.

<p align="center">
 <img src="../../_assets/robottype.PNG" width="70%"></img>
 <em><p align="center">Figure 3.1 Robot Type Selection Screen</p></em>
</p>

</br>
</br>
<p align="center">
 <img src="../../_assets/reboot.png" width="70%"></img>
 <em><p align="center">Figure 3.2 Controller Reboot Notification</p></em>
</p>

</br>

(3) Navigate to [System] → [5: Initialization] → [5: Additional axis parameter setting](../2-parameters/parameters.md)].
<p align="center">
 <img src="../../_assets/addaxes_menu.PNG" width="70%"></img>
 <em><p align="center">Figure 3.3 Additional Axis Parameter Setting Menu</p></em>
</p>

[__SOURCE](3-Setup/2-parameters/parameters.md)
## 3.2 Additional Axis Parameter Setting

(1) Check the `Additional axis parameter setting` screen as shown below.

<p align="center">
 <img src="../../_assets/addaxes.PNG" width="70%"></img>
 <em><p align="center">Figure 3.4 Additional Axis Parameter Setting</p></em>
</p>

(2) Configure the additional axis parameter.</br>
(3) Press `[OK]` to complete setting.

</br>

---

**[Additional Axis Parameter]**

(1) Axis specification

* Select the type of additional axis form the following options:
Base, Servogun, Positioner, Jig, Sealer
* When determining the additional axis specification, follow the logical order:
Base → Servogun→ Positioner → Jig → Sealer

(2) Axis structure: Select the motion type and direction of the additional axis.

* For linear base axes(moving axes):
  * X-axis: Forward/Backward movement
  * Y-axis: Left/Right movement
  * Z-axis: Up/Down movement
* If the base axis is not installed in the same direction as the robot coordinate system, select "Any" and do "Base axis calibration".
* Like linear base axes, circular base axes can also be set to Rx/Ry/Rz or selected as "Any" and do "Base axis calibration".
* For "Jig" or "Sealer", the control mode can be selected as either "position control" or "speed control". In speed control mode, the motor rotates according to the motor speed command.
* For "Servogun", refer to the [Spot Welding Function Manual](https://hrbook-hrc.web.app/#/view/doc-spot-weld/en/2-servo-gun-initial-setting/README).
* For "Positioner", refer to the [Positioner Synchronization Function Manual](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/en/README)

(3) Axis position:

* Allows the user to axis configuration of the additional axis.

|Axis Position Information | Setting Value |
|---|---|
| BD : '1'  | BD640 board number: 1~2  |
| Axis : '7' | BD640 #1 : 7~8 </br>BD640 #2 : 1~8  |

* If set to '1', '7', the 7th axis on BD640 board #1 is selected.

(4) Reduction Ratio:

* Enter the movement amount of the additional axis per motor revolution.
* For linear axes, enter the movement amount of the additional axis per motor revolution in mm.
* For circular axes, enter the movement amount of the additional axis per motor revolution in deg.
* The sign is determined based on the positive direction of the motor(the direction in which the encoder value increases).
  * If the axis movement direction matches the increasing coordinate value of the additional axis, set it to "+".
  * If the coordinate value decreases instead, set it to "-".
* Refer to the example below for clarification.
* Example 1: If a circular axis uses only a 1/100 reduction gear.
  * Since the axis rotates 360 degrees for 100 motor revolutions,
    * The reduction ratio is:
      +360 / 100 [deg/rev]
* Example 2: If a linear axis uses a 1/20 reduction gear and a rack and pinion with a PCD of 110mm,
  * Since the axis moves 110xPhi=345.5749 [mm] for 20 motor revolutions,
  * The reduction ratio is:
    +3455749 / 200000 [mm/rev]
* Example 3: If a linear axis uses a 1/5 reduction gear and a ball screw with a 5mm lead,
  * Since the axis moves 5mm for 5motor revolutions,
  * The reduction ratio is:
    +5 / 5 [mm/rev]

(5) Soft limit:

* Sets the effective operating range of additional axis
* For linear axes, set in millimeters [mm].
* For circular axes, set in degrees [deg].
* The values are applied in `[System] - 3:Robot parameter - 3: Software limit`.

(6) AMP Specifications:

* Select the AMP specifications to be used for the additional axis.
* Choose the IPM symbol and enter the Hall Sensor specifications as a number between 0-9 to specify the AMP type. The AMP specification format is as follows:

  <center>

  |IPM Capacity | Description |
  |:---:|:---:|
  |(medium) L  | (IPM current rating) 150A, (Hall Sensor current rating) 4V/75A |
  |(medium) X  | (IPM current rating) 100A, (Hall Sensor current rating) 4V/50A |
  |(medium) Y  | (IPM current rating) 750A, (Hall Sensor current rating) 4V/50A |
  |(medium) Z  | (IPM current rating) 50A, (Hall Sensor current rating) 4V/25A |
  |(small) A  | (IPM current rating) 30A, (Hall Sensor current rating) 4V/15A |
  |(small) D  | (IPM current rating) 10A, (Hall Sensor current rating) 4V/5A |

  </center>

* The rated capacity is determined by the IPM symbol and hall Sensor symbol.

  <center>

  |AMP Model | Code | Hall Sensor Specification| Full Scale Current (Im) |
  |:---:|:---:|:---:|:---:|
  |medium  | 0 | 4V/75A  |  140.62A|
  |medium  | 1 | 4V/50A  |  93.75A |
  |medium  | 2 | 4V/25A  |  46.87A |
  |medium  | 3 | 4V/15A  |  28.12A |
  |medium  | 4 | 4V/10A  |  18.75A |
  |medium  | 5 | 4V/5A   |  9.37A  |
  |small   | 3 | 4V/15A  |  27.27A |
  |small   | 4 | 4V/10A  |  18.18A |
  |small   | 5 | 4V/5A   |  9.19A  |
  |small   | 6 | 4V/3A   |  5.45A  |
  |small   | 7 | 4V/6A   |  10.91A |
  |small   | 8 | 4V/2A   |  3.64A  |
  |small   | 9 | 4V/1A   |  1.82A  |

</center>

(7) Motor Specifications:

* Select the motor specifications used for the additional axis.
* First, choose the motor capacity, then select the motor specification.
* If there are minor modifications to certain motor attributes, a revision number (rev) may be added to the motor model number. In such cases, it is recommended to select the latest motor version with the highest revision number.
  * Example:
    Among TSM3563N7020E731, TSM3563N7020E731_R1, and TSM3563N7020E731_R2, it is recommended to select TSM3563N7020E731_R2.

(8) Acceleration/Deceleration Parameters:

* Set the maximum speed and acceleration time for the additional axis.
* The values set here are applied in `[System] - 3: Robot parameter - 34: Accel and decel parameter`.
* While the maximum speed of the additional axis can be specified by the user, it is limited by the motor's rated speed.
* If vibration occurs during additional axis operation, the acceleration time should be adjusted accordingly.

[__SOURCE](3-Setup/3-mechanism/mechanism.md)
## 3.3 Mechanism Setting

(1) Mechanism setting

* Navigate to `[System] - 5: Initialization - 6: Mechanism Setting`.

<p align="center">
 <img src="../../_assets/mechanism.PNG" width="70%"></img>
 <em><p align="center">Figure 3.7 Mechanism Setting</p></em>
</p>

* The additional axis must have a mechanism group set in order to assign the jog key for manual mode. Robot axes are fixed to Mechanism M0. Additional axis can be classified from Mechanism M1 to M7.

</br>

(2) Parameter File Backup

* After completing the additional axis settings, copy the project file (hi6_proj.json) to a USB memory from `[Service] - 5: File manager`.

<p align="center">
 <img src="../../_assets/project.PNG" width="70%"></img>
 <em><p align="center">Figure 3.8 Setting File Backup</p></em>
</p>
[__SOURCE](4-Teaching-run/4_teaching_run.md)
# 4. Teaching & Run

[__SOURCE](4-Teaching-run/1-manual/manual.md)
## 4.1 Manual Mode (Jog)

(1) Pressing the [Mechanism] key at the top of the TP screen will change mechanism status to 1. it can be allow manual operation for Mechanism Group 1.

(2) Additional axis manual operation moves each axis individually, regardless of the coordinate system. However, for moving axes, movement depends on the selected coordinate system:

* Axis: Moves the moving axis individually in the set axis direction.
* Cartesian/Tool: The robot TCP position and orientation are fixed while moving axis moves.

(3) Manual operation speed (based on S8): 25% of the additional axis maximum speed (however, linear speed is limited to 250mm/sec)

</br>

{% hint style="info" %}

In the case of additional axes, they are installed arbitrarily based on user requirements. Therefore, They are not pre-tuned except for som standard models.

If there are issues with the control performance of an additional axis, [Additional axis autotuning](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/7-system/7-auto-calibration/7-Addaxis-autotuning) is required.

{% endhint %}


[__SOURCE](4-Teaching-run/2-run/run.md)
## 4.2 Run

(1) Interpolation Off</br>
Each axis reaches its target point simultaneously.

(2) Linear Interpolation</br>
The robot tool center point(TCP) moves with linear interpolation, maintaining its trajectory and orientation.

* The base axis moves in synchronization with the robot to ensure linear interpolation of the TCP.
* Other additional axes are not related to the robot TCP but reach their target points simultaneously.

(3) Circular Interpolation</br>
The robot tool center point(TCP) moves with circular interpolation, maintaining its trajectory and orientation.

* The base axis moves in synchronization with the robot to ensure circular interpolation of the TCP.
* Other additional axes are not related to the robot TCP, but reach their target positions simultaneously.

[__SOURCE](5-Manual-Tuning/README.md)
# 5. Manual Tuning of External Axes

This section describes the manual tuning of external axis servos.


### Specifications

(1) Tuning is available when the controller system is configured for up to 16 axes.
- In the case of a 6-axis robot, up to 10 external axes can be tuned.

(2) When in Engineering Mode (R314), the manual tuning function for external axes is activated in the UI. 

### Preparation
  
(1) Engineering Mode (R314)

(2) Job Files: The following files are required in the controller.

- 6000_axis_tun_sub_set_global_one_axis.job
- 6010_axis_tun_sub_set_tun_axis.job
- 6020_axis_tun_main_trq_ripple_mode1_one_axis.job
- 6040_axis_tun_sub_set_option_one_axis.job
- 6041_axis_tun_sub_set_pose_data_one_axis.job
- 6043_axis_tun_sub_run_high_spd_one_axis.job

(3) Warm Up the External Axis

The external axis should be warmed up to create an optimal tuning environment. The appropriate timing for tuning can be determined based on the encoder temperature. The checking method is as follows.

![](../_assets/enc_temp1_en.png)

Figure 3.9 Checking encoder temperature during manual tuning of an external axis


![](../_assets/enc_temp2_en.png)

Figure 3.10 Checking encoder temperature during manual tuning of an external axis


(4) Finding the Oscillation Gain

This is the process of finding the maximum gain value. The goal is to operate the robot using jog motion and identify the gain at which noise begins to occur.


![](../_assets/max_kv_en.png)

Figure 3.11 Finding the oscillation gain during manual tuning of an external axis

Once the oscillation gain is found, reduce Kv by half and apply it. This value becomes the initial gain value.


### Tuning Procedure

(1) 6010.job Program (Setup Job File)

* g_total_axis = Total number of axes configured in the controller
* g_cmd_axis = External axis number to be tuned
* g_start_angle = Start position for external axis tuning (Rotational axis: deg, Linear axis: mm)
* g_end_angle = End position for external axis tuning (Rotational axis: deg, Linear axis: mm)


#### Example

![](../_assets/6010_job_Window_en.png)

Figure 3.12 6010.job screen

![](../_assets/mechanism_window_en.png)

Figure 3.13 External axis mechanism screen


The total number of axes configured in the controller is 10 (6 robot axes + 4 external axes): g_total_axis = 10

To tune External Axis 2 (a_2, jig): g_cmd_axis = 8 (6 robot axes + External Axis 2)

Start/End position of External Axis 2 (a_2, jig): g_start_angle/g_end_angle should be set according to the soft limits and travel range. Here, it is configured to operate from -10 deg to 10 deg as an example.

* Note: If the travel range is too short, torque ripple values may not be output at high speed.

(2) Running 6020.job (Main job file for actual tuning)

6020.job must be executed after setting the total number of axes (g_total_axis), the axis to be tuned (g_cmd_axis), and the motion range (g_start_angle/g_end_angle) in 6010.job.

Run in 1Cycle mode at 100% playback speed.

When 6020.job is executed, it first checks the motion range at low speed.

After confirming the motion range, the program will stop due to a stop command within 6020.job. If there is no issue with the motion range, press Start to continue.
<br> 

(3) Checking Results (Screen: System → Axis Control Optimization → Torque Ripple Tuning)

![](../_assets/Trq_ripple_window_en.png)

Figure 3.14 Torque Ripple screen configuration

Note1. At lower speeds, the get holding time may take longer.

Note2. If the state is ON on the screen, press the 'Single Initialization' button to turn it OFF, then press the 'Execute' button.

<br>

The results can be checked as follows.

![](../_assets/Trq_ripple_Data_result1_en.png)

Figure 3.15 Result confirmation


(4) Tuning Completion Criteria

Torque ripple must not exceed 2% at any speed.
Position deviation should be maintained around 100 or less.
Noise and vibration must not occur.
Increase Kv repeatedly until the torque ripple approaches 2%.
Find the optimal Kv value that satisfies all of the above conditions simultaneously.<br>

<br>

(Reference) If noise or vibration occurs even when the torque ripple is below 2%, reduce Kv until noise and vibration no longer occur.

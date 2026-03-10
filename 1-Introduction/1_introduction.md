# 1. Introduction

This section explains the setup for additional axes except the basic robot axes.

{% hint style="info" %}
 The servo boards for each controller are as follows:<br>
 (Hi6 : BD640, Hi7 : BD642)
{% endhint %}  

</br>

### **[ Registration Procedure ]**

* Preparation Work  </br>
(1) Prepare the main unit (robot + additional axes) and wire harness  </br>
(2) Prepare the controller, one set of servo boards (required when applying additional axes of three or more), additional axis AMP, and signal cables  </br>
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

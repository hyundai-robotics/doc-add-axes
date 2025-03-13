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

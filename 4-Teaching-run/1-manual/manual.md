# 4.1 Manual Mode (Jog)

(1) Pressing the [Mechanism] key at the top of the TP screen will change mechanism status to 1. it can be allow manual operation for Mechanism Group 1.

(2) Additional axis manual operation moves each axis individually, regardless of the coordinate system. However, for moving axes, movement depends on the selected coordinate system:

* Axis: Moves the moving axis individually in the set axis direction.
* Cartesian/Tool: The robot TCP position and orientation are fixed while moving axis moves.

(3) Manual operation speed (based on S8): 25% of the additional axis maximum speed (however, linear speed is limited to 250mm/sec)

</br>
</br>
</br>

## 참고사항

In the case of additional axes, they are installed arbitrarily based on user requirements. Therefore, They are not pre-tuned except for som standard models.

If there are issues with the control performance of an additional axis, [Additional axis autotuning](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/korean-tp630/7-system/7-auto-calibration/7-Addaxis-autotuning) is required.



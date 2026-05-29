## 4.1 Manual Mode (Jog)

(1) Pressing the [Mechanism] key at the top of the TP screen will change mechanism status to 1. This allows for manual operation for Mechanism Group 1.

(2) Additional axis manual operation moves each axis individually, regardless of the coordinate system. However, for moving axes, movement depends on the selected coordinate system:

* Axis: Moves the moving axis individually in the set axis direction.
* Cartesian/Tool: The robot TCP position and orientation are fixed while moving axis moves.

(3) Manual operation speed (based on S8): 25% of the additional axis maximum speed (however, linear speed is limited to 250mm/sec)

</br>

{% hint style="info" %}

* In the case of additional axes, they are installed arbitrarily based on user requirements. Therefore, they are not pre-tuned except for some standard models.
* If there are performance issues with an additional axis, gain tuning is required.
* Please proceed with tuning using [Additional axis autotuning](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/7-system/7-auto-calibration/7-addaxis-autotuning?cont_model=${cont_model}).
* If the Additional axis autotuning process does not function smoothly, you can utilize [Additional Axis Manual Tuning](./../../5-Manual-Tuning/README.md).

{% endhint %}


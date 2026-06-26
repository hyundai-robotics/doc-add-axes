## 4.1 手动模式 (Jog)

(1) 按下 TP 屏幕顶部的 [Mechanism] 键将机制状态更改为 1。这允许对机制组 1 进行手动操作。

(2) 附加轴手动操作独立移动每个轴，而不考虑坐标系统。然而，对于移动轴，运动取决于所选坐标系统：

* 轴：以设定轴方向单独移动移动轴。
* 笛卡尔/工具：在移动轴移动时，机器人 TCP 位置和方向是固定的。

(3) 手动操作速度（基于 S8）：附加轴最大速度的 25%（但是，线速度限制为 250mm/sec）

</br>

{% hint style="info" %}

* 在附加轴的情况下，它们是根据用户需求随意安装的。因此，除了某些标准模型之外，它们没有预调。
* 如果附加轴存在性能问题，则需要增益调节。
* 请使用 [附加轴自调节](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/zh-tp630/7-system/7-auto-calibration/7-addaxis-autotuning?cont_model=${cont_model}) 进行调节。
* 如果附加轴自调节过程无法顺利进行，您可以利用 [附加轴手动调节](./../../5-Manual-Tuning/README.md)。

{% endhint %}
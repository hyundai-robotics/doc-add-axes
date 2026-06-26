
[__SOURCE](README.md)
# ${cont_model} 控制器操作手册 - 额外轴
[__SOURCE](0-about-this-manual/README.md)
# 关于手册
[__SOURCE](0-about-this-manual/precautions.md)
# 注意事项

{% include file="zh/precautions.md" %}
[__SOURCE](0-about-this-manual/safety-notice.md)
# 安全警告

{% include file="zh/safety-notice.md" %}
[__SOURCE](1-Introduction/README.md)
<script id="page-config" type="application/json">
{
	"permittedStrs": ["Hi6", "Hi7"]
}
</script>

# 1. 引言

本节解释了除基本机器人轴之外的附加轴的设置。

{% hint style="info" %}
 每个控制器的伺服板如下：<br>
 (Hi6 : BD640, Hi7 : BD642)
{% endhint %}  

</br>

### **[ 注册程序 ]**

* 准备工作  </br>
(1) 准备主机（机器人 + 附加轴）和线束  </br>
(2) 准备控制器、一套伺服板（在申请三个或更多的附加轴时需要）、附加轴AMP和信号电缆  </br>
(3) 附加轴参数  </br>
    准备附加轴的输入数据，包括轴规格、配置、减速比、电机和AMP，以适用于附加轴设置的格式（参考第3.2节）。  </br>
(4) 附加轴加速/减速时间  </br>
准备输入附加轴的指令加速/减速时间所需的数据（参考第3.2节）。 </br>

* 机器人类型和附加轴参数的注册  </br>
在主机和控制器之间连接线束后，初始化系统，选择机器人类型，输入附加轴数量，然后输入附加轴参数（最大可控轴数：16，包括机器人）  </br>
* 如果机器人类型和附加轴参数在出厂前已注册，则可以跳过此过程。  </br>

* 连接和检查  </br>
关闭控制器 → 连接主机和控制器之间的必要电缆 → 打开控制器 → 设置伺服系统的编码器校准和参考位置（轴参数）。  </br>

* 完成  </br>
配置附加轴操作环境后，将 hi6_proj.json 文件保存到外部存储设备（USB内存）。
[__SOURCE](2-Presetting/README.md)
<script id="page-config" type="application/json">
{
	"permittedStrs": ["Hi6", "Hi7"]
}
</script>

# 2. 预设

* 检查要连接的组件和材料。
* 确保准备好预先计算的数据和选择的附加轴信息。
(减速比、AMP规格、电动机规格、最高速度、加速度时间等。)
* 根据附加轴的数量，伺服板和AMP的组合如下。

  | 轴配置 | BD/AMP配置 |
  | :------------------: | :-------------------: |
    | 1到6轴</br>(基本上是6轴) | 1个伺服板</br>1个AMP(6轴类型) |
  | 7到8轴</br>(基本上是6轴 + 2个附加轴) | 1个伺服板</br>1个AMP(6轴类型)</br>1到2个AMP(1轴类型) |
  | 9到12轴</br>(基本上是6轴 + 6个附加轴) | 2个伺服板</br> 2个AMP(6轴类型) |
  | 13到16轴</br>(基本上是6轴 + 12个附加轴) | 2个伺服板</br>2个AMP(6轴类型)</br>1到4个AMP(1轴类型) |

{% hint style="info" %}
 每个控制器的伺服板如下：<br>
 (Hi6 : BD640, Hi7 : BD642)
{% endhint %}  

</br>

* 接口板的DIP开关设置 (BD6H0) 根据附加轴的数量.(* 仅限Hi6)
  <div align="left">

  | 名称 | 目的 | 设置|
  | :------------------: | :-------------------: | :-------------------: |
  | SW1 | 配置SSM1的开关 (BD640板 1) | 当SSM1连接时：开关1/2/3/4关闭 </br> 当SSM1断开时：开关1/2/3/4打开 |
  | SW2 | 配置SSM2的开关 (BD640板 2) | 当SSM2连接时：开关1/2/3/4关闭 </br> 当SSM2断开时：开关1/2/3/4打开 |
  | SW3 | 配置SSM3的开关 (BD640板 3) | 当SSM3连接时：开关1/2/3/4关闭 </br> 当SSM3断开时：开关1/2/3/4打开 |
  | SW4 | 配置SSM4的开关 (BD640板 4) | 当SSM4连接时：开关1/2/3/4关闭 </br> 当SSM4断开时：开关1/2/3/4打开 |

<p align="center">
  <img src="../_assets/2_1_dip_switch_example.jpg" width="500">
  <em><p align="center">图2.1 DIP开关示例 (SSM1已连接)</p></em>
</p>
  </div>

{% hint style="info" %}
每个伺服板最多可以控制8个轴，提供两种类型的AMP（6轴类型和1轴类型）。

{% endhint %}
[__SOURCE](3-Setup/README.md)
# 3. 机器人类型和附加轴参数设置
[__SOURCE](3-Setup/1-robottype/robottype.md)
## 3.1 设置机器人类型和附加轴数量

附加轴的设置按以下顺序进行：

(1) 导航到 [System] → [5: Initialization] → [2: Robot type selection] 并选择机器人类型。

{% hint style="info" %}
要配置机器人类型和附加轴参数设置，必须输入工程师代码 (R314)。显示器屏幕右上角的“e”指示灯确认工程师代码已输入。
{% endhint %}

(2) 输入附加轴的数量并按“OK”，然后重启控制器。

<p align="center">
 <img src="../../_assets/robottype.PNG" width="70%"></img>
 <em><p align="center">图 3.1 机器人类型选择界面</p></em>
</p>

</br>
</br>
<p align="center">
 <img src="../../_assets/reboot.PNG" width="70%"></img>
 <em><p align="center">图 3.2 控制器重启通知</p></em>
</p>

</br>

(3) 导航到 [System] → [5: Initialization] → [5: Additional axis parameter setting](../2-parameters/parameters.md)].
<p align="center">
 <img src="../../_assets/addaxes_menu.PNG" width="70%"></img>
 <em><p align="center">图 3.3 附加轴参数设置菜单</p></em>
</p>
[__SOURCE](3-Setup/2-parameters/parameters.md)
<script id="page-config" type="application/json">
{
	"permittedStrs": ["Hi6", "Hi7"]
}
</script>

## 3.2 附加轴参数设置

(1) 检查下面所示的 `附加轴参数设置 (Additional axis parameter setting)` 屏幕。

<p align="center">
 <img src="../../_assets/addaxes.PNG" width="70%"></img>
 <em><p align="center">图 3.4 附加轴参数设置</p></em>
</p>

(2) 配置附加轴参数。</br>
(3) 按 `[OK]` 完成设置。

</br>

---

**[附加轴参数]**

(1) 轴规格

* 从以下选项中选择附加轴的类型：
基座、伺服枪、定位器、夹具、密封器
* 确定附加轴规格时，请遵循逻辑顺序：
基座 → 伺服枪 → 定位器 → 夹具 → 密封器

(2) 轴结构：选择附加轴的运动类型和方向。

* 对于线性基座轴（移动轴）：
  * X轴：前/后移动
  * Y轴：左/右移动
  * Z轴：上/下移动
* 如果基座轴的安装方向与机器人坐标系统不同，请选择“任何”并进行“基座轴校准”。
* 像线性基座轴一样，圆形基座轴也可以设置为 Rx/Ry/Rz，或选择“任何”并进行“基座轴校准”。
* 对于“夹具”或“密封器”，可以选择控制模式为“位置控制”或“速度控制”。在速度控制模式下，电机根据电机速度命令旋转。
* 对于“伺服枪”，请参阅 [点焊功能手册](https://hrbook-hrc.web.app/#/view/doc-spot-weld/zh/2-servo-gun-initial-setting/README?cont_model=${cont_model})。
* 对于“定位器”，请参阅 [定位器同步功能手册](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/zh/README?cont_model=${cont_model})

(3) 轴位置：

* 允许用户配置附加轴的轴。

{% hint style="info" %}
 每个控制器的伺服板如下：<br>
 (Hi6 : BD640, Hi7 : BD642)
{% endhint %} 

|轴位置信息 | 设置值 |
|---|---|
| BD : '1'  | 伺服板号码：1~2  |
| 轴 : '7' | 伺服板 #1 : 7~8 </br>伺服板 #2 : 1~8  |

* 如果设置为 '1' 和 '7'，则在伺服板 #1 上选择第 7 轴。

(4) 减速比：

* 输入每次电机旋转时附加轴的运动量。
* 对于线性轴，输入每次电机旋转时附加轴的运动量（单位为 mm）。
* 对于圆形轴，输入每次电机旋转时附加轴的运动量（单位为 deg）。
* 符号根据电机的正方向决定（编码器值增加的方向）。
  * 如果轴运动方向与附加轴的坐标值增加方向相符合，则设为“+”。
  * 如果坐标值反而减小，则设为“-”。
* 请参阅下面的示例以获得澄清。
* 示例 1：如果圆形轴仅使用 1/100 的减速齿轮。
  * 因为轴每 100 次电机旋转旋转 360 度，
    * 减速比为：
      +360 / 100 [deg/rev]
* 示例 2：如果线性轴使用 1/20 的减速齿轮和 PCD 为 110mm 的齿轮齿条，
  * 因为轴在 20 次电机旋转中移动 110xPhi=345.5749 [mm]，
  * 减速比为：
    +3455749 / 200000 [mm/rev]
* 示例 3：如果线性轴使用 1/5 的减速齿轮和传动螺杆，导程为 5mm，
  * 因为轴在 5 次电机旋转中移动 5mm，
  * 减速比为：
    +5 / 5 [mm/rev]

(5) 软限制：

* 设置附加轴的有效操作范围。
* 对于线性轴，以毫米 [mm] 设置。
* 对于圆形轴，以度 [deg] 设置。
* 这些值在 `[System] - 3:机器人参数 - 3: 软件限制 ([System] - 3:Robot parameter - 3: Software limit)` 中应用。

(6) AMP 规格：

* 选择用于附加轴的 AMP 规格。
* 选择 IPM 符号，并输入霍尔传感器规格，作为介于 0-9 之间的数字，以指定 AMP 类型。AMP 规格格式如下：

  <center>

  |IPM 容量 | 描述 |
  |:---:|:---:|
  |(中) L  | (IPM 当前评级) 150A, (霍尔传感器当前评级) 4V/75A |
  |(中) X  | (IPM 当前评级) 100A, (霍尔传感器当前评级) 4V/50A |
  |(中) Y  | (IPM 当前评级) 750A, (霍尔传感器当前评级) 4V/50A |
  |(中) Z  | (IPM 当前评级) 50A, (霍尔传感器当前评级) 4V/25A |
  |(小) A  | (IPM 当前评级) 30A, (霍尔传感器当前评级) 4V/15A |
  |(小) D  | (IPM 当前评级) 10A, (霍尔传感器当前评级) 4V/5A |

  </center>

* 额定容量由 IPM 符号和霍尔传感器符号决定。

  <center>

  |AMP 型号 | 代码 | 霍尔传感器规格| 满量程电流 (Im) |
  |:---:|:---:|:---:|:---:|
  |中  | 0 | 4V/75A  |  140.62A|
  |中  | 1 | 4V/50A  |  93.75A |
  |中  | 2 | 4V/25A  |  46.87A |
  |中  | 3 | 4V/15A  |  28.12A |
  |中  | 4 | 4V/10A  |  18.75A |
  |中  | 5 | 4V/5A   |  9.37A  |
  |小   | 3 | 4V/15A  |  27.27A |
  |小   | 4 | 4V/10A  |  18.18A |
  |小   | 5 | 4V/5A   |  9.19A  |
  |小   | 6 | 4V/3A   |  5.45A  |
  |小   | 7 | 4V/6A   |  10.91A |
  |小   | 8 | 4V/2A   |  3.64A  |
  |小   | 9 | 4V/1A   |  1.82A  |

</center>

(7) 电机规格：

* 选择用于附加轴的电机规格。
* 首先选择电机容量，然后选择电机规格。
* 如果某些电机属性有小的修改，可以在电机型号后添加修订号（rev）。在这种情况下，建议选择修订号最高的最新电机版本。
  * 示例：
    在 TSM3563N7020E731、TSM3563N7020E731_R1 和 TSM3563N7020E731_R2 中，建议选择 TSM3563N7020E731_R2。

(8) 加速度/减速度参数：

* 设置附加轴的最大速度和加速时间。
* 此处设置的值在 `[System] - 3: 机器人参数 - 34: 加减速参数 ([System] - 3: Robot parameter - 34: Accel and decel parameter)` 中应用。
* 虽然附加轴的最大速度可以由用户指定，但它受电机额定速度的限制。
* 如果在附加轴操作过程中发生振动，应相应地调整加速时间。
[__SOURCE](3-Setup/3-mechanism/mechanism.md)
## 3.3 机构设置

(1) 机构设置

* 导航到 `[System] - 5: 初始化 - 6: Mechanism Setting ([System] - 5: Initialization - 6: Mechanism Setting)`.

<p align="center">
 <img src="../../_assets/mechanism.PNG" width="70%"></img>
 <em><p align="center">图 3.7 机构设置</p></em>
</p>

* 附加轴必须有一个机构组才能为手动模式分配操纵键。机器人轴固定在机构 M0。附加轴可以从机构 M1 分类到 M7。

</br>

(2) 参数文件备份

* 在完成附加轴设置后，从 `[Service] - 5: 文件管理器 ([Service] - 5: File manager)` 将项目文件 (hi6_proj.json) 复制到 USB 存储器。

<p align="center">
 <img src="../../_assets/project.PNG" width="70%"></img>
 <em><p align="center">图 3.8 设置文件备份</p></em>
</p>
[__SOURCE](4-Teaching-run/README.md)
# 4. 教学与运行
[__SOURCE](4-Teaching-run/1-manual/manual.md)
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
[__SOURCE](4-Teaching-run/2-run/run.md)
## 4.2 运行

(1) 插值关闭</br>
每个轴同时到达其目标点。

(2) 线性插值</br>
机器人工具中心点(TCP)以线性插值移动，保持其轨迹和方向。

* 基座轴与机器人同步移动，以确保TCP的线性插值。
* 其他附加轴与机器人TCP无关，但同时到达其目标点。

(3) 圆形插值</br>
机器人工具中心点(TCP)以圆形插值移动，保持其轨迹和方向。

* 基座轴与机器人同步移动，以确保TCP的圆形插值。
* 其他附加轴与机器人TCP无关，但同时到达其目标位置。
[__SOURCE](5-Manual-Tuning/README.md)
# 5. 手动调节外部轴

本节描述了外部轴伺服的手动调节。


### 规格

(1) 当控制器系统配置为最多 16 个轴时，可以进行调节。
- 在六轴机器人情况下，可以调节最多 10 个外部轴。

(2) 在工程模式 (R314) 下，用户界面中激活外部轴的手动调节功能。 

### 准备
  
(1) 工程模式 (R314)

(2) 作业文件：控制器中需要以下文件。

- 6000_axis_tun_sub_set_global_one_axis.job
- 6010_axis_tun_sub_set_tun_axis.job
- 6020_axis_tun_main_trq_ripple_mode1_one_axis.job
- 6040_axis_tun_sub_set_option_one_axis.job
- 6041_axis_tun_sub_set_pose_data_one_axis.job
- 6043_axis_tun_sub_run_high_spd_one_axis.job

(3) 预热外部轴

外部轴应进行预热，以创建最佳调节环境。调节的合适时机可根据编码器温度确定。检查方法如下。

![](../_assets/enc_temp1_en.png)

图 3.9 在手动调节外部轴时检查编码器温度


![](../_assets/enc_temp2_en.png)

图 3.10 在手动调节外部轴时检查编码器温度


(4) 寻找振荡增益

这是找到最大增益值的过程。目标是使用 jog 动作操作机器人，并识别噪声开始出现时的增益。


![](../_assets/max_kv_en.png)

图 3.11 在手动调节外部轴时寻找振荡增益

一旦确定振荡增益，将 Kv 减半并应用。此值成为初始增益值。


### 调节程序

(1) 6010.job 程序 (设置作业文件)

* g_total_axis = 在控制器中配置的总轴数
* g_cmd_axis = 要调节的外部轴编号
* g_start_angle = 外部轴调节的起始位置 (旋转轴：度，线性轴：毫米)
* g_end_angle = 外部轴调节的结束位置 (旋转轴：度，线性轴：毫米)


#### 示例

![](../_assets/6010_job_Window_en.png)

图 3.12 6010.job 屏幕

![](../_assets/mechanism_window_en.png)

图 3.13 外部轴机制屏幕


在控制器中配置的总轴数为 10 (6 个机器人轴 + 4 个外部轴)：g_total_axis = 10

要调节外部轴 2 (a_2, jig)：g_cmd_axis = 8 (6 个机器人轴 + 外部轴 2)

外部轴 2 (a_2, jig) 的起始/结束位置：g_start_angle/g_end_angle 应根据软限制和行程范围进行设置。这里配置为从 -10 度到 10 度操作为例。

* 注意：如果行程范围过短，高速时可能无法输出扭矩涟漪值。

(2) 运行 6020.job (实际调节的主作业文件)

在 6010.job 中设置总轴数 (g_total_axis)、要调节的轴 (g_cmd_axis) 和运动范围 (g_start_angle/g_end_angle) 后，必须执行 6020.job。

以 100% 回放速度在 1Cycle 模式下运行。

当执行 6020.job 时，首先以低速检查运动范围。

确认运动范围后，程序将因 6020.job 中的停止命令而停止。如果运动范围没有问题，请按开始继续。

<br> 

(3) 检查结果 (屏幕：系统 → 轴控制优化 → 扭矩涟漪调节)

![](../_assets/Trq_ripple_window_en.png)

图 3.14 扭矩涟漪屏幕配置

注释1. 在较低速度下，获得保持时间可能会更长。

注释2. 如果屏幕上的状态为 ON，请按下“单次初始化”按钮将其关闭，然后按下“执行”按钮。

<br>

结果可以如下检查。

![](../_assets/Trq_ripple_Data_result1_en.png)

图 3.15 结果确认


(4) 调节完成标准

在任何速度下扭矩涟漪不得超过 2%。
位置偏差应维持在 100 或更低。
不得出现噪声和振动。
反复增加 Kv，直到扭矩涟漪接近 2%。
找到同时满足以上所有条件的最佳 Kv 值。<br>

<br>

(参考) 如果在扭矩涟漪低于 2% 时仍然出现噪声或振动，请减小 Kv，直到不再出现噪声和振动。
# 定高模式（多旋翼）

[<img src="../../assets/site/difficulty_easy.png" title="飞行难度：简单" width="30px" />](../getting_started/flight_modes.md#key_difficulty)&nbsp;[<img src="../../assets/site/remote_control.svg" title="需要手动/遥控器控制" width="30px" />](../getting_started/flight_modes.md#key_manual)&nbsp;[<img src="../../assets/site/altitude_icon.svg" title="需要高度传感器（例如气压计、测距仪）" width="30px" />](../getting_started/flight_modes.md#altitude_only)

_高度模式_是一个_相对_容易的遥控模式，其中滚转和俯仰控制机体在左右和前后方向上的运动（相对于机体“前方”），偏航摇杆控制水平面上的旋转速度，油门控制升降速度。

当摇杆被释放/回中时，机体将恢复水平和保持当前的_高度_。 如果在水平面上运动，飞机将继持续运动直到任何动量被风阻力消散。 如果刮风，飞机会向风的方向漂移。

:::tip
_高度模式_ 是新飞手最安全的非GPS 手动模式。 就像[手动/自稳](../flight_modes_mc/manual_stabilized.md)模式，但是在松开摇杆时也可以锁定机体高度。
:::

下图直观的显示了模式行为（对于一个[模式 2 发送器](../getting_started/rc_transmitter_receiver.md#transmitter_modes)）。

![高度控制MC - Mode2 RC控制器](../../assets/flight_modes/altitude_control_mode_copter.png)

## 技术摘要

遥控/手动模式就像 [手动/自稳（多旋翼）](../flight_modes_mc/manual_stabilized.md)模式，但具有_高度稳定_ （摇杆中位能够使无人机水平并且保持固定高度）。

- 回正摇杆（内带死区）：
  - RPY摇杆使飞机水平。
  - 油门（~50%）抗风保持当前姿态。
- 外部中心：
  - 翻滚/俯仰摇杆控制各自方向的倾斜角，导致左右和前后的移动。
  - 油门摇杆以预定的最大速率（和其他轴上的移动速度）控制上升速度。
  - 偏航摇杆控制水平面上方的角度旋转速率。
- 起飞：
  - 降落时，如果将油门杆抬高至 62.5%（从油门杆最低开始的整个范围），无人机将起飞。

:::note

- 需要手动输入（遥控器，或者通过 MAVLink 连接的游戏手柄/拇指摇杆）。
- 通常使用气压计测量高度，在极端天气条件下可能会变的不准确。 带有激光雷达/距离传感器的飞机将能够以更高的可靠性和准确性控制高度。
:::

## 参数

该模式受以下参数影响：

| 参数                                                                                                          | 描述                                                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <a id="MPC_Z_VEL_MAX_UP"></a>[MPC_Z_VEL_MAX_UP](../advanced_config/parameter_reference.md#MPC_Z_VEL_MAX_UP) | 最大垂直上升速度。 默认：3m/s。                                                                                                                                                                         |
| <a id="MPC_Z_VEL_MAX_DN"></a>[MPC_Z_VEL_MAX_DN](../advanced_config/parameter_reference.md#MPC_Z_VEL_MAX_DN) | 最大垂直下降速度。 默认：1m/s。                                                                                                                                                                         |
| <a id="RCX_DZ"></a>`RCX_DZ`                                                                           | 通道 X 的遥控死区。 油门的 X 值取决于 [ RC_MAP_THROTTLE ](../advanced_config/parameter_reference.md#RC_MAP_THROTTLE) 的值。 例如，如果油门是通道4，则[ RC4_DZ ](../advanced_config/parameter_reference.md#RC4_DZ)指定死区。 |
| <a id="MPC_xxx"></a>`MPC_XXXX`                                                                         | 大多数 MPC_xxx参数会影响此模式下的飞行行为（至少在某种程度上）。 例如，[MPC_THR_HOVER](../advanced_config/parameter_reference.md#MPC_THR_HOVER)定义飞机悬停时的推力。                                                              |

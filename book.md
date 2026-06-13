
[__SOURCE](README.md)
# ${cont_model} 功能手册 - 定位器同步.
[__SOURCE](0-about-this-manual/README.md)
# 关于手册

[__SOURCE](0-about-this-manual/precautions.md)
# 注意事项

{% include file="zh/precautions.md" %}
[__SOURCE](0-about-this-manual/safety-notice.md)
# 安全注意事项

{% include file="zh/safety-notice.md" %}

[__SOURCE](1-intro/README.md)
# 1. 概述

位置器同步功能使机器人能够相对于安装在机器人外部的外部夹具单元进行线性或圆周运动。应用于位置器同步功能的外部夹具单元称为位置器，也称为工作站。

应用此功能可以弥补由于机器人的工作区域限制而导致的工作限制。换句话说，即使工件固定在位置器上，位置器移动，机器人也会跟踪这一移动，并在工件上执行线性或圆周运动。

主要功能规格如下：
| **主要特征规格** | **特征** |
| - | - |
| 位置器组 | 支持组 1~4 |
| 位置器轴 | 支持1轴、2轴位置器（直接驱动，旋转） |
| 插值方法 | 支持线性、圆周插值 |


<br/>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="../_assets/1_0_1.png" alt="1-axis rotation positioner" width="97%" />
      <br />
      <em>图 1.0.1. 1轴旋转位置器</em>
    </td>
    <td align="center" width="50%">
      <img src="../_assets/1_0_2.png" alt="2-axis rotation positioner" width="100%" />
      <br />
      <em>图 1.0.2. 2轴旋转位置器</em>
    </td>
  </tr>
</table>
[__SOURCE](1-intro/1-1-major-functions.md)
# 1.1 主要特点

* <mark style="color:green;">**多组定位器**</mark>

  通过将夹具设置为附加轴作为定位器组进行控制。可以注册总共三个定位器组，每个组最多可以设置两个轴的定位器。

* <mark style="color:green;">**位置校准**</mark>

  为定位器设置坐标系统，定位器的校准通过旋转的1轴进行3点校准，1轴直动定位器进行2点校准，以及2轴直动定位器进行5点校准。

* <mark style="color:green;">**教学**</mark>

  定位器独立操作功能的教学设计为通过选择附加轴键切换到机器人正交坐标系、定位器同步慢 jog、附加轴操作等，方便教学定位器同步操作命令(smov)。

* <mark style="color:green;">**执行**</mark>

  定位器同步特性支持线性和圆形插补。当执行同步操作命令(smov)时，它在定位器上运行插补操作。
[__SOURCE](1-intro/1-2-operation-sequence.md)
# 1.2 操作顺序


<p align="center">
 <img src="../_assets/1_2_1_en.png" width="60%"></img>
 <em><p align="center">图 1.2.1. 操作顺序</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/README.md)
# 2. 系统设置
[__SOURCE](2-system_settings/2-1-system-initialization.md)
# 2.1 系统初始化

1. 在第一次设置控制器时，请执行系统初始化。
  导航到 `System > 5: Initialization > 1: System format` 并按下初始化按钮。

<!-- ![](../_assets/2_1_1.png) -->
<p align="center">
 <img src="../_assets/2_1_1_en.png" width="60%"></img>
 <em><p align="center">图 2.1.1. 系统初始化</p></em>
</p>   
</br>

2. 在系统初始化后，选择机器人类型。
  一旦选择了机器人类型，下面将显示屏幕。输入将要使用的附加轴的总数。完成设置后，请按确认按钮。

<p align="center">
 <img src="../_assets/2_1_2_en.png" width="60%"></img>
 <em><p align="center">图 2.1.2. 选择机器人类型</p></em>
</p>   
</br>

<!-- ![](../_assets/2_1_2.png)
![](../_assets/2_1_3.png) -->

3. 开启控制器电源。

<p align="center">
 <img src="../_assets/2_1_3_en.png" width="60%"></img>
 <em><p align="center">图 2.1.3. 重启</p></em>
</p>

4. 控制器启动后，导航到 `System > 5: Initialization > 5: Additional axis parameter setting` 以配置附加轴。
  在此屏幕上，通过将轴规格选择为“定位器”来设置与定位器相对应的附加轴，并配置相关参数。
  根据定位器轴的配置，选择线性或旋转轴。
  对于线性轴，如果知道定位器轴相对于机器人基坐标的操作方向，请相应指定方向。如果确切方向未知，可以随意选择。
  对于旋转轴，如果定位器不是制造商提供的标准件，请将轴配置设置为“自定义”，并配置其余参数。
  有关配置附加轴的详细说明，请参阅 [附加轴功能用户手册](https://hrbook-hrc.web.app/#/view/doc-add-axes/en/README?cont_model=${cont_model})。

<!-- ![](../_assets/2_1_4.png)
![](../_assets/2_1_5.png) -->
<p align="center">
 <img src="../_assets/2_1_4_en.png" width="60%"></img>
 <em><p align="center">图 2.1.4. 线性轴参数配置</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_5_en.png" width="60%"></img>
 <em><p align="center">图 2.1.5. 旋转轴参数配置</p></em>
</p>  
5. 如果定位器由我们的公司提供，请从轴配置列表中选择相应的项目。
  在这种情况下，无需配置任何其他参数。

<p align="center">
 <img src="../_assets/2_1_6_en.png" width="60%"></img>
 <em><p align="center">图 2.1.6. 标准参数配置</p></em>
</p>   
</br>

<!-- ![](../_assets/2_1_6.png) -->

6. 导航到 `System > 4: 应用参数 > 3: 定位器同步` 以配置定位器组。
  作为示例，配置了一个 2 轴定位器和两个 1 轴定位器。
  由于需要三个站，因此需要添加站。单击 '+' 按钮将在列表窗口中创建站。
  选择每个站并输入额外的轴数以配置该站。对于 1 轴定位器，仅在第一个字段中输入额外的轴数。
  在下图中，额外轴 a1 和 a2 对应于站 1 的 2 轴定位器，a3 对应于站 2 的 1 轴定位器，a4 对应于站 3 的 1 轴定位器。

<!-- ![](../_assets/2_1_7.png)  
![](../_assets/2_1_8.png)  
![](../_assets/2_1_9.png)   -->
<p align="center">
 <img src="../_assets/2_1_7_en.png" width="60%"></img>
 <em><p align="center">图 2.1.7. 额外轴 a1, a2 设置</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_8_en.png" width="60%"></img>
 <em><p align="center">图 2.1.8. 额外轴 a3 设置</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_9_en.png" width="60%"></img>
 <em><p align="center">图 2.1.9. 额外轴 a4 设置</p></em>
</p>   
</br>

7. 导航到 `System > 5: 初始化 > 6: 机制设置` 以配置每个站的定位器的 jogging 机制。  

<!-- ![](../_assets/2_1_10.png) -->
<p align="center">
 <img src="../_assets/2_1_10_en.png" width="60%"></img>
 <em><p align="center">图 2.1.10. 机制设置</p></em>
</p>   
</br>


8. 重启控制器以正确应用额外轴、站和机制设置。

[__SOURCE](2-system_settings/2-2-robot-calibration.md)
# 2.2 机器校准

请参阅以下内容: [${cont_model} 控制器操作手册 7.7 自动校准](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/7-system/7-auto-calibration/README?cont_model=${cont_model})
[__SOURCE](2-system_settings/2-3-positioner-calibration/README.md)
# 2.3 位置器校准

- 位置器校准是一种自动计算位置器的位置和运动方向的功能，使用机器人的 TCP 姿态。因此，为了从位置器校准中获得准确的结果，必须精确输入机器人的 TCP 姿态。作为初步步骤，可以利用 "`System > 6: Auto Calibration > Optimize axis origin and tool length`" 功能。

- 要使用位置器校准，必须为位置器轴分配一个组号。一个位置器组可以由最多 2 个轴组成，这些轴可以配置为旋转-旋转或线性-线性。

- 位置器校准的基本原理是，对于由旋转轴构成的位置器，使用三个教学点的位置来形成一个圆，以计算旋转轴的位置。因此，每个旋转轴需要三个教学点来计算其中心。对于具有旋转轴的双轴位置器，使用一个共同的中间点，总共需要五个教学点，以计算每个旋转轴的位置和方向。对于由线性轴构成的位置器，由于仅计算轴方向，因此每个轴需要两个教学点。对于双轴线性位置器，共享中间点，从三个教学点计算每个轴的方向。

- 程序教学后，可以从设置屏幕执行位置器校准或通过执行 ```posi_calib``` 过程。
[__SOURCE](2-system_settings/2-3-positioner-calibration/1_1axis-positioner-calibration-teaching.md)
# 2.3.1 教导 1-Axis 位置器校准程序

1. 选择要教授的程序。

2. 对于 1-Axis 位置器，在位置器上固定一个尖锐的教学点。将此教学点尽可能远离旋转中心，以提高校准精度，非常重要。

3. 将位置器大约旋转 30° 在一个方向上，并精确地教授三个点以记录程序。教学方法在下图中说明。对于线性位置器，使用相同的方法尽可能远地教授两个点。

4. 教学时，尽量保持机器人的姿态一致。

<!-- ![](../../_assets/image9.png) -->

<p align="center">
 <img src="../../_assets/2_3_1.png"></img>
 <em><p align="center">图 2.3.1. 教导 1-Axis 位置器的校准</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/2_2axis-positioner-calibration-teaching.md)
# 2.3.2 教学 2 轴定位器校准程序

1. 选择要教授的程序。

2. 将尖端教学点尽可能远离旋转中心。

3. 对于 2 轴定位器，类似于 1 轴定位器，首先仅移动 2 轴并教授三个点。
   然后，从第 3 个教学点（S3）开始，仅移动 1 轴以教授第 4（S4）和第 5（S5）个点。
   对于线性定位器，在 2 轴上教授两个点，然后移动 1 轴并教授一个点。

4. 教学时，尽量保持机器人姿态的一致性。

<!-- ![](../../_assets/image10.png) -->

<p align="center">
 <img src="../../_assets/2_3_2.png" width="70%"></img>
 <em><p align="center">图 2.3.2. 教学 2 轴定位器校准</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/3_positioner-calibration-execution.md)
# 2.3.3 执行定位器校准

1. 进入 `System > 4: Application parameters > 3: Positioner synchronization`。
2. 选择要校准的站点并点击校准按钮以输入教授的程序编号。

<!-- ![](../../_assets/image11.png) -->
<p align="center">
 <img src="../../_assets/2_3_3_en.png" width="60%"></img>
 <em><p align="center">图 2.3.3. 执行定位器校准</p></em>
</p>   
</br>

3. 校准结果将显示在屏幕上。按右侧的 `[OK]` 按钮以确认数据设置。

<!-- ![](../../_assets/image12.png) -->
<p align="center">
 <img src="../../_assets/2_3_4_en.png" width="60%"></img>
 <em><p align="center">图 2.3.4. 定位器校准结果</p></em>
</p>   
</br>

4. 如果用户知道来自 CAD 数据的定位器的确切位置，可以手动设置定位器的位置和 DH 参数。按下 `[OK]` 按钮将相应地应用数据设置。

5. 您可以通过以下链接验证校准是否正确执行： [`3.2 Positioner Synchronized Jog Mode`](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/en/3-manual-operation/3_2-positioner-sync-jog-mode?cont_model=${cont_model})
[__SOURCE](2-system_settings/2-3-positioner-calibration/4_posi_calib.md)
# 2.3.4 posi_calib

此命令执行位置器校准，使位置器与机器人同步操作。

### 描述

通常，通过设置对话框执行位置器校准。然而，当由于伺服工具更换而更改位置器时，必须在机器人操作期间更新校准。此命令用于在机器人程序中执行校准。

您可以在以下链接验证校准是否正确执行：[3.2 位置器同步慢速模式](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/en/3-manual-operation/3_2-positioner-sync-jog-mode?cont_model=${cont_model})

### 语法

```python
posi_calib job=<calibration prog. no.>,s_=<station no.>
```

### 参数
<table>
  <thead>
    <tr>
      <th style="text-align:left">项目</th>
      <th style="text-align:left">含义</th>
      <th style="text-align:left">备注</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">校准程序编号</td>
      <td style="text-align:left">
        位置器校准程序编号
        (1 ~ 9999)
      </td>
      <td style="text-align:left">变量</td>
    </tr>
    <tr>
      <td style="text-align:left">站点编号</td>
      <td style="text-align:left">
        需要校准的站点编号
      </td>
      <td style="text-align:left">变量</td>
    </tr>
  </tbody>
</table>

### 示例
```python
          # 位置器校准程序 (9995.job)
     S1   move P,spd=100%,accu=1,tool=0 # 位置器校准的教学
     S2   move P,spd=100%,accu=1,tool=0 # 位置器校准的教学
     S3   move P,spd=100%,accu=1,tool=0 # 位置器校准的教学
```
```python
          # 工具更换 + 定位器校准
     S1   move P,spd=100%,accu=1,tool=0 
          toolchng on,tg=P1,di=1        # 工具更换
          posi_calib job=9995,s_=1      # 定位器校准
```
[__SOURCE](3-manual-operation/README.md)
# 3. 手动操作

有两种方法可以移动定位器： <br/>
- 独立移动：单独移动定位器。
- 同步移动：在机器人同步移动以跟随定位器时移动定位器。
[__SOURCE](3-manual-operation/3_1-positioner-independent-jog-mode.md)
# 3.1 定位器独立操作模式

独立操作模式通过在教学挂件上按“mech.”键进行切换。设置为此模式时，定位器可以独立操作，如下所示。

<!-- ![](../_assets/image13.png) -->
<p align="center">
 <img src="../_assets/3_1_1_en.png" width="60%"></img>
 <em><p align="center">图 3.1.1. 定位器独立操作方法</p></em>
</p>   
</br>

- 定位器机制：J7 + J8
- 坐标系统：轴坐标系统（独立操作）
- 记录条件：一般移动命令
[__SOURCE](3-manual-operation/3_2-positioner-sync-jog-mode.md)
# 3.2 定位器同步移动模式

定位器同步移动模式仅在完成定位器校准后可用。
在定位器独立移动模式下，按下教学 pendant 上的 "crd.sys" 按钮将显示 "Synchronized S1"。在此模式下，当定位器移动时，机器人跟随定位器的移动并执行同步移动。

<!-- ![](../_assets/image14.png) -->
<p align="center">
 <img src="../_assets/3_1_2_en.png" width="60%"></img>
 <em><p align="center">图 3.1.2. 定位器同步移动方法</p></em>
</p>   
</br>

- 定位器机制：J7 + J8
- 坐标系统：同步坐标系统（同步移动）
- 记录条件：smov 命令

<!-- ![](../_assets/image14-1.png) -->
<p align="center">
 <img src="../_assets/3_1_3.png" width="60%"></img>
 <em><p align="center">图 3.1.3. 定位器操作仿真</p></em>
</p>   
</br>
[__SOURCE](4-program-creation/README.md)
# 4. 编程
[__SOURCE](4-program-creation/4-1-step-recording.md)
# 4.1 步骤记录

- 在位置器独立的慢动模式下，程序记录条件被设置为移动命令。
- 在位置器同步的慢动模式下，记录条件被设置为smov命令，以支持位置器同步命令。
[__SOURCE](4-program-creation/4-2-smov.md)
# 4.2 smov

```py
	smov {station number}, {interpolation method}, {speed}, {accuracy}, {tool number}
```

- smov 命令的设置是在定位器坐标系统内确定的。
  例如，当定位器移动时，沿直线移动两个点时，速度是指 TCP 相对于定位器的运动速度。

1. 站号：指的是定位器组号 (S1 ~ S4)。
2. 插值方法：可以对工件进行线性 (L) 或圆形 (C) 插值。
3. 速度：设置机器人 TCP 在工件上移动的速度。
4. 精度：设置工件上线性和圆形插值的精度。
5. 工具号：设置用于操作的机器人工具号。
[__SOURCE](4-program-creation/4-3-positioner-linear-interpolation-example.md)
# 4.3 教学线性插值在定位器上的示例

1. 确定工件上的起始点和目标点。

<!-- ![](../_assets/image15.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_1.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.1. 第 1 步
  </em>
</p>
<br/>

2. 使用机机制键和坐标系，选择定位器并移动它。然后，使用机制键切换回机器人，并将机器人工具尖端对准所需的起始点。在此状态下，按“记录(record)”键以记录移动命令（如有必要，请使用 smov）。

3. 使用机制键和坐标系将模式设置为定位器同步走动。如果所使用的定位器是站 1，请选择坐标系为“sync. S1”。

<!-- ![](../_assets/image16.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_2.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.2. 第 2~3 步
  </em>
</p>
<br/>

4. 当选择主控时，如果将定位器移动到所需位置，机器人将保持其相对于定位器上的工作起始点的位置和方向。

<!-- ![](../_assets/image17.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_3.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.3. 第 4 步
  </em>
</p>
<br/>

5. （注意）在此状态下，定位器上的某一点与机器人工具尖端之间的误差是由于机器人和定位器之间的校准误差。然而，在回放时不会出现此误差作为轨迹误差。换句话说，即使存在一些误差，再次将机器人移动到目标位置并使用 smov 记录将导致在回放时最小的轨迹位置误差。

6. 将机制切换回机器人，然后使用走动键将机器人移动到目标点（S2）并对齐。

<!-- ![](../_assets/image18.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_4.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.4. 第 6 步
  </em>
</p>
<br/>
7. 要记录同步步骤（smov），请将模式重新设置为定位器同步 jog，并选择坐标系统为同步 S1，然后按下“记录（record）”键以记录 smov 步骤。

8. 按照步骤 ③→④→⑤ 进行后续步骤。

<!-- ![](../_assets/image19.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_5.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.5. 第 7~8 步
  </em>
</p>
<br/>

9. 当记录的程序执行时，定位器移动，机器人相对于定位器上的工件执行线性插补。

<!-- ![](../_assets/image20.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_6.png" width="50%" style="display: block;" />
  <em style="display: block; text-align: center; width: 50%; auto;">
    图 4.1.6. 第 9 步
  </em>
</p>
<br/>

`注意 (Caution)`
1) 记录定位器同步步骤（smov）不必完全遵循上述方法。  
   您可以独立移动机器人和定位器来设置位置和方向，然后将步骤记录为 smov。  
   机器人将根据相对于定位器上工件的指定插补方法进行移动。

2) 如果两个连续的 smov 步骤都使用线性插补（“L”），则将像移动命令那样进行拐角运动。

3) 在 smov 步骤中设置的速度是工作速度。  
   因此，即使定位器移动较多，如果记录步骤之间在工件上的工作距离非常短，定位器的工作速度可能实际上变为无限（∞），导致其以最大速度移动。  
   要限制定位器在这种情况下的速度，请将速度单位设置为“SEC”。  
   这意味着步骤运动是基于时间而不是速度，因此即使工件上的距离为零（0），移动时间也会被指定。  
<br/><br/>

`编程示例`
```py

    S1   move  L,spd=60%,accu=1,tool=0        # 接近起始位置步骤
    S2   smov  S1,L,spd=100mm/s,accu=1,tool=0    # 定位器同步线性插补
    S3   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S4   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S5   move  P,spd=10%,accu=1,tool=0        # 后退步骤（与定位器异步）
    S6   move  L,spd=200mm/s,accu=1,tool=0 
    end

```

[__SOURCE](5-add-axis-move-independent-execution/README.md)
# 5. 独立执行附加轴移动

独立附加轴移动功能使附加轴能够根据外部输入信号独立于机器人执行移动命令。
[__SOURCE](5-add-axis-move-independent-execution/5-1-system-setting.md)
# 5.1 系统设置

1. 导航到 `系统 - 应用程序参数 - 命令独立执行 (系统 - 应用程序参数 - 命令独立执行)`。  
![](../_assets/5_1_1_en.png)  
    - 输入信号  
    配置信号输入到控制器。

    - 命令  
    指定当输入信号从关（OFF）变为开（ON）时要执行的命令。对于定位器的独立操作，使用移动命令。  

    - 执行中的输出信号  
    当指定命令的执行开始时，此信号变为开（ON），当执行完成时变为关（OFF）。  

    - 执行完成后的输出信号  
    当指定命令的执行开始时，此信号变为关（OFF），当执行完成时变为开（ON）。  
    有关独立命令执行的更多详细信息，请参阅 [${cont_model} 控制器操作手册 - 7.5.10 命令独立执行](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/7-system/5-application-parameter/10-cmd-idp-exe?cont_model=${cont_model}).  

2. 在命令字段中，按下面的按钮输入移动命令。要独立执行额外轴的移动，必须在移动命令中指定机制。  
    有关输入移动命令的更多详细信息，请参阅 [${cont_model} 控制器操作手册 - 机器人语言 HRScript - 5.1 姿势](https://hrbook-hrc.web.app/#/view/doc-hrscript/en/5-moving-robot/1-pose?cont_model=${cont_model}).  

3. 使用 axisctrl off 命令设置要独立操作的轴。axisctrl 命令用于选择额外轴是否由任务程序控制。设置为 axisctrl off 的轴不会移动到任务程序中记录的位置，并且可以独立移动。设置为 axisctrl on 的轴按照任务程序中记录的位置移动。  
    通过外部输入信号独立执行移动命令仅在 axisctrl off 和 axisctrl on 之间的部分有效。当在 axisctrl off 活动时接收到在独立命令执行中指定的输入信号，移动命令将被执行。设置为 axisctrl off 的轴以黄色文本显示，例如下图顶部所示的 j_7。  
    ![](../_assets/5_1_2_en.png)  
    有关更多详细信息，请参阅 [${cont_model} 控制器手册 - 多任务处理 - 2.1.6 axisctrl](https://hrbook-hrc.web.app/#/view/doc-multi-task/en/2-related-function/2-1-command-sentence/6-axisctrl?cont_model=${cont_model}).  


{% hint style="warning" %}  

1. 用于独立命令执行的移动命令中指定的机制必须仅由设置为 axisctrl off 的轴组成。

2. 如果在独立执行完成之前执行了 axisctrl on 命令，将发生错误 **'E1455 (轴 0) 独立操作未完成'**，并且机器人轴将停止。在这种情况下，独立操作的轴将继续移动到其目标位置。  

    这发生是因为机器人任务程序的执行时间短于独立移动命令的执行时间。相应地修改程序，或在 axisctrl on 命令之前插入等待命令，以检查独立执行完成信号是否已输出。

{% endhint %}
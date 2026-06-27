
[__SOURCE](README.md)
# ${cont_model} 功能手册 - 位置器同步.
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

Positioner Synchronization Function 使机器人能够相对于安装在机器人外部的外部夹具单元执行线性或圆周运动。应用于位置器同步功能的外部夹具单元称为位置器，也称为站点。

应用这些功能可以补偿由机器人的工作区域限制引起的工作限制。换句话说，即使工件固定在位置器上，而位置器移动，机器人也会跟踪这个运动并在工件上执行线性或圆周运动。

关键功能规格如下： 
| **关键特性规格** | **特性** |
| - | - |
| 位置器组 | 支持 1~4 组 |
| 位置器轴 | 支持 1 轴、2 轴位置器（直接驱动，旋转） |
| 插值方法 | 支持线性、圆形插值 |

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

<!-- 
| <img src="../_assets/1_0_1.png" height="447px" width="357px"> | <img src="../_assets/1_0_2.png" height="447px" width="357px"> |
|:-: | :-:|             
|1轴旋转位置器|  2轴旋转位置器   |
 -->
[__SOURCE](1-intro/1-1-major-functions.md)
# 1.1 关键特性

* <mark style="color:green;">**多组定位器**</mark>

  通过将夹具设置为额外轴作为定位器组进行控制。总共可以注册三组定位器，每组最多可以设置为2轴定位器。

* <mark style="color:green;">**位置校准**</mark>

  为了设置定位器的坐标系统，定位器的校准通过旋转1轴的3个点、1轴直动定位器的2个点，以及2轴直动定位器的5个点进行。

* <mark style="color:green;">**教学**</mark>

  定位器独立操作功能的教学设计为可通过选择额外轴键切换到机器人正交坐标系统、定位器同步慢走、额外轴操作等，这对于教学定位器同步操作命令(smov)非常方便。

* <mark style="color:green;">**执行**</mark>

  定位器同步特性支持线性和圆形插补。当执行同步操作命令(smov)时，在定位器上运行插补操作。
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

1. 第一次设置控制器时，执行系统初始化。
  导航至 `System > 5: Initialization > 1: System format` 并按下初始化按钮。

<!-- ![](../_assets/2_1_1.png) -->
<p align="center">
 <img src="../_assets/2_1_1_en.png" width="60%"></img>
 <em><p align="center">图 2.1.1. 系统初始化</p></em>
</p>   
</br>

2. 系统初始化后，选择机器人类型。
  一旦选择了机器人类型，下面将显示屏幕。输入要使用的附加轴的总数。完成设置后，按下确认按钮。

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

4. 控制器启动后，导航至 `System > 5: Initialization > 5: Additional axis parameter setting` 配置附加轴。
  在此屏幕上，通过选择轴规格为“Positioner”并配置相关参数来设置对应于定位器的附加轴。
  根据定位器轴的配置，选择线性或旋转轴。
  对于线性轴，如果已知定位器轴相对于机器人基坐标的操作方向，请相应地指定方向。如果确切方向未知，请任意选择。
  对于旋转轴，若定位器不是制造商提供的标准型，则将轴配置设置为“Custom”，并配置剩余参数。
  有关配置附加轴的详细说明，请参阅 [附加轴功能用户手册](https://hrbook-hrc.web.app/#/view/doc-add-axes/zh/README?cont_model=${cont_model})。

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
</br>

5. 如果定位器是我们公司提供的，请从轴配置列表中选择相应的项目。
  在这种情况下，无需配置其他参数。

<p align="center">
 <img src="../_assets/2_1_6_en.png" width="60%"></img>
 <em><p align="center">图 2.1.6. 标准参数配置</p></em>
</p>   
</br>

<!-- ![](../_assets/2_1_6.png) -->

6. 导航至 `System > 4: Application parameters > 3: Positioner synchronization` 配置定位器组。
  作为示例，配置一个2轴定位器和两个1轴定位器。
  由于需要三个站点，您需要添加站点。点击“+”按钮将在列表窗口中创建站点。
  选择每个站点并输入附加轴编号以配置站点。对于1轴定位器，仅在第一个字段中输入附加轴编号。
  在下图中，附加轴 a1 和 a2 对应于站点 1 的2轴定位器，a3 对应于站点 2 的1轴定位器，a4 对应于站点 3 的1轴定位器。

<!-- ![](../_assets/2_1_7.png)  
![](../_assets/2_1_8.png)  
![](../_assets/2_1_9.png)   -->
<p align="center">
 <img src="../_assets/2_1_7_en.png" width="60%"></img>
 <em><p align="center">图 2.1.7. 附加轴 a1, a2 设置</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_8_en.png" width="60%"></img>
 <em><p align="center">图 2.1.8. 附加轴 a3 设置</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_9_en.png" width="60%"></img>
 <em><p align="center">图 2.1.9. 附加轴 a4 设置</p></em>
</p>   
</br>

7. 导航至 `System > 5: Initialization > 6: Mechanism Settings` 配置每个站点的定位器操控机制。  

<!-- ![](../_assets/2_1_10.png) -->
<p align="center">
 <img src="../_assets/2_1_10_en.png" width="60%"></img>
 <em><p align="center">图 2.1.10. 机制设置</p></em>
</p>   
</br>


8. 请重启控制器以正确应用附加轴、站点和机制设置。
[__SOURCE](2-system_settings/2-2-robot-calibration.md)
# 2.2 机器人校准

请参阅以下内容: [${cont_model} 控制器操作手册 7.7 自动校准](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/zh-tp630/7-system/7-auto-calibration/README?cont_model=${cont_model})
[__SOURCE](2-system_settings/2-3-positioner-calibration/README.md)
# 2.3 定位器校准

- 定位器校准是一种通过使用机器人的 TCP 姿态，自动计算定位器位置和移动方向的功能。因此，为了从定位器校准中获得准确的结果，机器人 TCP 姿态必须精确输入。作为初步步骤，可以利用“`System > 6: Auto Calibration > Optimize axis origin and tool length`”功能。

- 要使用定位器校准，必须为定位器轴分配一个组号。一个定位器组可以包含多达 2 个轴，可以配置为旋转-旋转或线性-线性。

- 定位器校准的基本原理是，对于由旋转轴组成的定位器，使用三个教学点的位置来形成一个圆，以计算旋转轴的位置。
  因此，每个旋转轴需要三个教学点来计算各个旋转轴的中心。
  在具有旋转轴的双轴定位器的情况下，使用一个共同的中间点，总共需要五个教学点，以计算每个旋转轴的位置和方向。
  对于由线性轴组成的定位器，由于仅计算轴的方向，每个轴需要两个教学点。
  对于一个双轴线性定位器，共享中间点，并从三个教学点计算每个轴的方向。

- 在程序教学之后，可以从设置屏幕或通过执行```posi_calib```程序进行定位器校准。
[__SOURCE](2-system_settings/2-3-positioner-calibration/1_1axis-positioner-calibration-teaching.md)
# 2.3.1 教学 1-Axis 位置器校准程序

1. 选择要教学的程序。

2. 对于 1-Axis 位置器，在位置器上固定一个尖端教学点。将这个教学点尽可能远离旋转中心以提高校准准确性是很重要的。

3. 将位置器在一个方向上旋转约 30°，并精确地教学三个点以记录程序。教学方法如下面的图所示。
  对于线性位置器，使用相同的方法教学两个尽可能远的点。

4. 教学时，尽量保持机器人的姿态一致。

<p align="center">
 <img src="../../_assets/2_3_1.png"></img>
 <em><p align="center">图 2.3.1. 教学 1-Axis 位置器校准</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/2_2axis-positioner-calibration-teaching.md)
# 2.3.2 教学 2-轴定位器校准程序


1. 选择要教学的程序。

2. 尽可能将指向的教学点放置在离旋转中心最远的位置。

3. 对于 2-轴定位器，类似于 1-轴定位器，首先仅移动 2-轴并教学三个点。
  然后，从第三个教学点(S3)开始，仅移动 1-轴以教学第四(S4)和第五(S5)点。
  对于线性定位器，先在 2-轴上教学两个点，然后移动 1-轴并教学一个点。

4. 教学时，尽量保持机器人的姿态一致。


<p align="center">
 <img src="../../_assets/2_3_2.png" width="70%"></img>
 <em><p align="center">图 2.3.2. 教学 2-轴定位器校准</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/3_positioner-calibration-execution.md)
# 2.3.3 执行定位器校准

1. 进入 `System > 4: Application parameters > 3: Positioner synchronization`。
2. 选择要校准的站，并单击校准按钮以输入教导程序编号。

<p align="center">
 <img src="../../_assets/2_3_3_en.png" width="60%"></img>
 <em><p align="center">图 2.3.3. 执行定位器校准</p></em>
</p>   
</br>

3. 校准结果将显示。按右侧的 `[OK]` 按钮以最终确定数据设置。

<p align="center">
 <img src="../../_assets/2_3_4_en.png" width="60%"></img>
 <em><p align="center">图 2.3.4. 定位器校准结果</p></em>
</p>   
</br>

4. 如果用户知道 CAD 数据中定位器的确切位置，可以手动设置定位器的位置和 DH 参数。按下 `[OK]` 按钮将相应地应用数据设置。

5. 您可以通过以下链接验证校准是否正确执行： [`3.2 位置器同步走动模式`](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/zh/3-manual-operation/3-2-positioner-sync-jog-mode?cont_model=${cont_model})
[__SOURCE](2-system_settings/2-3-positioner-calibration/4_posi_calib.md)
# 2.3.4 posi_calib

此命令执行位置器校准，以使位置器能够与机器人同步操作。


### 描述

通常，通过设置对话框执行位置器校准。然而，当由于伺服工具更换导致位置器更改时，必须在机器人操作期间更新校准。此命令用于在机器人程序中执行校准。

您可以在以下链接验证校准是否正确执行：[3.2 位置器同步走动模式](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/zh/3-manual-operation/3-2-positioner-sync-jog-mode?cont_model=${cont_model})


### 语法

```python
posi_calib job=<校准程序编号>,s_=<站点编号>
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
        需校准的站点编号
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
          # 工具更换 + 位置器校准
     S1   move P,spd=100%,accu=1,tool=0 
          toolchng on,tg=P1,di=1        # 工具更换
          posi_calib job=9995,s_=1      # 位置器校准
```
[__SOURCE](3-manual-operation/README.md)
# 3. 手动操作

有两种方式可以移动定位器： <br/>
- 独立移动：单独移动定位器。
- 同步移动：在机器人同步移动以跟随定位器的同时移动定位器。
[__SOURCE](3-manual-operation/3-1-positioner-independent-jog-mode.md)
# 3.1 位置器独立操作模式

独立操作模式通过按下教导 pendant 上的 "mech." 按键切换。当设置为此模式时，位置器可以独立操作，如下所示。

<p align="center">
 <img src="../_assets/3_1_1_en.png" width="60%"></img>
 <em><p align="center">图 3.1.1. 位置器独立操作方法</p></em>
</p>   
</br>

- 位置器机制: J7 + J8
- 坐标系统: 轴坐标系统（独立操作）
- 记录条件: 一般移动命令
[__SOURCE](3-manual-operation/3-2-positioner-sync-jog-mode.md)
# 3.2 位置器同步 jog 模式

位置器同步 jog 模式仅在完成位置器校准后可用。
在位置器独立 jog 模式下，按下教学挂件上的“crd.sys”按钮将显示“Synchronized S1”。在此模式下，当位置器移动时，机器人会跟随位置器的运动并执行同步 jogging。

<p align="center">
 <img src="../_assets/3_1_2_en.png" width="60%"></img>
 <em><p align="center">图 3.1.2. 位置器同步 jog 方法</p></em>
</p>   
</br>

- 位置器机制：J7 + J8
- 坐标系统：同步坐标系统（同步 jog）
- 记录条件：smov 命令

<p align="center">
 <img src="../_assets/3_1_3.png" width="60%"></img>
 <em><p align="center">图 3.1.3. 位置器操作仿真</p></em>
</p>   
</br>
[__SOURCE](4-program-creation/README.md)
# 4. 编程
[__SOURCE](4-program-creation/4-1-step-recording.md)
# 4.1 步骤记录

- 在定位器独立的手动模式下，程序记录条件设置为移动命令。
- 在定位器同步的手动模式下，记录条件设置为 smov 命令，以支持定位器同步命令。
[__SOURCE](4-program-creation/4-2-smov.md)
# 4.2 smov

```py
	smov {station number}, {interpolation method}, {speed}, {accuracy}, {tool number}
```

- smov命令的设置是在定位器坐标系统内决定的。
  例如，当定位器移动时，在两点之间直线移动，速度指的是TCP相对于定位器的移动速度。

1. 站号：指定位器组号（S1 ~ S4）。
2. 插值方法：可对工件执行线性(L)或圆形(C)插值。
3. 速度：设置机器人TCP在工件上的移动速度。
4. 精度：设置对工件进行线性和圆形插值的精度。
5. 工具号：设置用于操作的机器人工具号。
[__SOURCE](4-program-creation/4-3-positioner-linear-interpolation-example.md)
# 4.3 在定位器上教学线性插值的示例

1. 确定工件上的起始点和目标点。

<p style="text-align: left;">
  <img src="../_assets/4_1_1.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.1. 第一步
  </em>
</p>
<br/>

2. 使用机制键和坐标系统，选择定位器并移动它。然后，使用机制键切换回机器人，将机器人工具末端对准所需的起始点。在此状态下，按下“记录(record)”键以记录移动命令（如有必要使用smov）。

3. 使用机制键和坐标系统将模式设置为定位器同步走动。如果使用的定位器是站 1，选择坐标系统为“sync. S1”。

<p style="text-align: left;">
  <img src="../_assets/4_1_2.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.2. 第二步~第三步
  </em>
</p>
<br/>

4. 当主控被选中时，如果你将定位器移动到所需位置，机器人将保持其相对于定位器上的工作起始点的位置和方向。

<p style="text-align: left;">
  <img src="../_assets/4_1_3.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.3. 第四步
  </em>
</p>
<br/>

5. （注意）在此状态下，定位器上的某个点与机器人工具末端之间的误差是由于机器人和定位器之间的校准误差。然而，在回放过程中，这种误差不会表现为轨迹误差。换句话说，即使存在一些误差，再次将机器人移动到目标位置并使用smov记录，将会在回放过程中产生最小的轨迹位置误差。

6. 切换机制回到机器人，然后使用走动键将机器人移动到目标点（S2）并对齐。

<p style="text-align: left;">
  <img src="../_assets/4_1_4.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.4. 第六步
  </em>
</p>
<br/>

7. 要记录同步步骤（smov），将模式重新设置为定位器同步走动，选择坐标系统为同步 S1，然后按下“REC(record)”键以记录smov步骤。

8. 按照步骤 ③→④→⑤ 进行后续步骤。

<p style="text-align: left;">
  <img src="../_assets/4_1_5.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    图 4.1.5. 第七步~第八步
  </em>
</p>
<br/>


9. 当录制的程序被执行时，定位器移动，机器人相对于定位器上的工件执行线性插值。

<p style="text-align: left;">
  <img src="../_assets/4_1_6.png" width="50%" style="display: block;" />
  <em style="display: block; text-align: center; width: 50%; auto;">
    图 4.1.6. 第九步
  </em>
</p>
<br/>


`注意事项 (Caution)`
1) 记录定位器同步步骤（smov）不一定要遵循上述确切的方法。
  你可以独立移动机器人和定位器以设置位置和方向，然后将步骤记录为smov。
  机器人将根据指定的插值方法相对于定位器上的工件移动。

2) 如果两个连续的smov步骤都使用线性插值（“L”），则将执行与移动命令相同的转角动作。

3) 在smov步骤中设置的速度是工作速度。
  因此，即使定位器移动幅度很大，如果录制的步骤之间在工件上的工作距离非常短，定位器的工作速度可能有效地变为无限(∞)，导致其以最大速度移动。
  为了在这种情况下限制定位器速度，将速度单位设置为“SEC”。
  这意味着步骤移动是基于时间，而不是速度，因此即使工件上的距离为零(0)，移动时间也是被指定的。
<br/><br/>


`编程示例`
```py

    S1   move  L,spd=60%,accu=1,tool=0        # 接近起始位置步骤
    S2   smov  S1,L,spd=100mm/s,accu=1,tool=0    # 定位器同步线性插值
    S3   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S4   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S5   move  P,spd=10%,accu=1,tool=0        # 收回步骤（与定位器异步）
    S6   move  L,spd=200mm/s,accu=1,tool=0 
    end

```
[__SOURCE](5-add-axis-move-independent-execution/README.md)
# 5. 独立执行附加轴移动

独立附加轴移动功能使附加轴能够根据外部输入信号独立于机器人执行移动命令。
[__SOURCE](5-add-axis-move-independent-execution/5-1-system-setting.md)
# 5.1 系统设置

1. 导航到 `系统 - 应用程序参数 - 独立执行命令 (System - Application Parameter - Command Independent execution)`。  
![](../_assets/5_1_1_en.png)  
    - 输入信号  
    配置输入信号到控制器。

    - 命令  
    指定当输入信号从 OFF 变为 ON 时要执行的命令。独立操作位置器时，使用移动命令。  

    - 执行中的输出信号  
    当指定的命令执行开始时，此信号打开，执行完成时关闭。  

    - 执行完成后的输出信号  
    当指定的命令执行开始时，此信号关闭，执行完成时打开。  
    有关独立命令执行的更多详细信息，请参阅 [${cont_model} 控制器操作手册 - 7.5.10 独立命令执行](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/zh-tp630/7-system/5-application-parameter/10-cmd-idp-exe?cont_model=${cont_model})。  
  
2. 在命令字段中，按下面的按钮输入移动命令。要独立执行额外轴的移动，必须在移动命令中指定机制。  
    有关输入移动命令的更多详细信息，请参阅 [${cont_model} 控制器操作手册 - 机器人语言 HRScript - 5.1 位姿](https://hrbook-hrc.web.app/#/view/doc-hrscript/zh/5-moving-robot/1-pose?cont_model=${cont_model})。  

3. 使用 axisctrl off 命令设置要独立操作的轴。axisctrl 命令用于选择额外轴是否由任务程序控制。设置为 axisctrl off 的轴不会移动到任务程序中记录的位置，可以独立移动。设置为 axisctrl on 的轴根据任务程序中记录的位置移动。  
    通过外部输入信号独立执行移动命令仅在 axisctrl off 和 axisctrl on 之间的部分有效。当在 axisctrl off 活动时收到指定为独立命令执行的输入信号时，执行移动命令。设置为 axisctrl off 的轴显示为黄色文本，如下图顶部所示的 j_7。  
    ![](../_assets/5_1_2_en.png)  
    有关更多详细信息，请参阅 [${cont_model} 控制器手册 - 多任务处理 - 2.1.6 axisctrl](https://hrbook-hrc.web.app/#/view/doc-multi-task/zh/2-related-function/2-1-command-sentence/6-axisctrl?cont_model=${cont_model})。  


{% hint style="warning" %}  

1. 独立命令执行中指定的移动命令的机制必须只由设置为 axisctrl off 的轴组成。

2. 如果在独立执行完成之前执行 axisctrl on 命令，将发生错误 **'E1455 (Axis 0) 独立操作未完成'**，机器人轴将停止。在这种情况下，独立操作的轴将继续移动到其目标位置。  

    这种情况发生是因为机器人任务程序的执行时间短于独立移动命令的执行时间。相应修改程序，或在 axisctrl on 命令之前插入等待命令，以检查独立执行完成信号是否已输出。

{% endhint %}
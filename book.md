
[__SOURCE](README.md)
# ${cont_model} Function Manual - positioner sync.

[__SOURCE](0-about-this-manual/precautions.md)
# Precautions

{% include file="en/precautions.md" %}

[__SOURCE](1-intro/README.md)
# 1. Overview

Positioner Synchronization Function enables the robot to follow or perform linear or circular movements relative to an external jig unit installed outside the robot. This external jig unit appied to the positioner synchronization function is called the positioner, also known as the station.

Applying this functions can compensate for work limitations caused by the robot's retricted working area. In other words, even if the workpiece is fixed on the positioner and the positioner moves, the robot tracks this movement and performs linear or circular movements on the workpiece.

Key functional specifications are as follows: 
| **Key Feature Specifications** | **Features** |
| - | - |
| Positioner Group | Group 1~4 Support |
| Positioner axis | 1-axis, 2-axis Positioner Support(direct drive, rotation) |
| Interpolation method | Support for linear, circular interpolation |


<br/>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="../_assets/1_0_1.png" alt="1-axis rotation positioner" width="97%" />
      <br />
      <em>Figure 1.0.1. 1-axis rotation positioner</em>
    </td>
    <td align="center" width="50%">
      <img src="../_assets/1_0_2.png" alt="2-axis rotation positioner" width="100%" />
      <br />
      <em>Figure 1.0.2. 2-axis rotation positioner</em>
    </td>
  </tr>
</table>

<!-- 
| <img src="../_assets/1_0_1.png" height="447px" width="357px"> | <img src="../_assets/1_0_2.png" height="447px" width="357px"> |
|:-: | :-:|             
|1축 회전 포지셔너|  2축 회전 포지셔너   |
 -->

[__SOURCE](1-intro/1-1-major-functions.md)
# 1.1 Key Features

* <mark style="color:green;">**Multi-group Positioner**</mark>

  Control by setting the jig set as an additional axis as a positioner group. A total of three groups of positioners can be registered, each group can be set up to 2-axis positioners.

* <mark style="color:green;">**position calibration**</mark>

  To set the coordinate system for the positioner, calibration of the positioner is carried out through 3-points for the rotating 1-axis, 2-points for the 1-axis direct-acting positioner, and 5-points for the 2-axis direct-acting positioner.

* <mark style="color:green;">**Teaching**</mark>

  The teaching of the positioner independent operation function is designed to be switched to robot orthogonal coordinate system, positioner synchronous jog, additional axis operation, etc. by the selection of additional axis keys, which is convenient for teaching positioner synchronous operation commands(smov).

* <mark style="color:green;">**Execution**</mark>

  The positioner synchronization feature supports both linear and circular interpolation. When a synchronous operation command(smov) is executed, it is played running an interpolation operation on the positioner.
  
[__SOURCE](1-intro/1-2-operation-sequence.md)
# 1.2 Operation Order


<p align="center">
 <img src="../_assets/1_2_1_en.png" width="60%"></img>
 <em><p align="center">Figure 1.2.1. Operation order</p></em>
</p>   
</br>

[__SOURCE](2-system_settings/README.md)
# 2. System Settings
[__SOURCE](2-system_settings/2-1-system-initialization.md)
# 2.1 System Initialization

1. When setting up the controller for the first time, perform a system initialization.
  navigate to `System > 5: Initialization > 1: System format` and press the initialize button.

<!-- ![](../_assets/2_1_1.png) -->
<p align="center">
 <img src="../_assets/2_1_1_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.1. System Initialization</p></em>
</p>   
</br>

2. After System Initialization, select the robot type.
  Once the robot type is selected, the screen shown bellow will apper. Enter the total number of additional axes to be used. After completing the settings, press the Confirm button.

<p align="center">
 <img src="../_assets/2_1_2_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.2. Robot type Select</p></em>
</p>   
</br>

<!-- ![](../_assets/2_1_2.png)
![](../_assets/2_1_3.png) -->

3. Power on the controller.

<p align="center">
 <img src="../_assets/2_1_3_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.3. Reboot</p></em>
</p>

4. After the controller boots up, navigate to `System > 5: Initialization > 5: Additional axis parameter setting` to configure the additional axes.
  On this screen, set the additional axes corresponding to positioners by selecting the axis specification as "Positioner" and configure the relevant parameters.
  Depending on the configuration of the positioner axis, select either linear or rotary axis.
  For linear axis, if the operating direction of the positioner axis is known relative to the robot base coordinates, specify the direction accordingly. If the exact direction is unknown, select arbitrarily.
  For rotary axis, if the positioner is not a standard one provided by the manufacturer, set the axis configuration to "Custom" and configure the remaining parameters.
  For detailed instructions on configuring additional axes, please refer to the [Additional Axis Function User Manual](https://hrbook-hrc.web.app/#/view/doc-add-axes/en/README?cont_model=${cont_model}).


<!-- ![](../_assets/2_1_4.png)
![](../_assets/2_1_5.png) -->
<p align="center">
 <img src="../_assets/2_1_4_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.4. Linear Axis Parameter Configuration</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_5_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.5. Rotary Axis Parameter Configuration</p></em>
</p>   
</br>

5. If the positioner is provided by our company, select the corresponding item from the axis configuration list.
  In this case, there is no need to configure any other parameters.

<p align="center">
 <img src="../_assets/2_1_6_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.6. Standard Parameter Configuration</p></em>
</p>   
</br>

<!-- ![](../_assets/2_1_6.png) -->

6. Navigate to `System > 4: Application parameters > 3: Positioner synchronization` to configure the positioner groups.
  As an example, one 2-axis positioner and two 1-axis positioners are configured.
  Since three stations are required, you need to add stations. Clicking the '+' button will create stations in the list window.
  Select each station and enter the additional axis number to configure the station. For 1-axis positioners, enter the additional axis number only in the first field.
  In the figure below, additional axes a1 and a2 correspond to the 2-axis positioner at Station 1, a3 corresponds to the 1-axis positioner at Station 2, and a4 corresponds to the 1-axis positioner at Station 3.

<!-- ![](../_assets/2_1_7.png)  
![](../_assets/2_1_8.png)  
![](../_assets/2_1_9.png)   -->
<p align="center">
 <img src="../_assets/2_1_7_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.7. Additional Axis a1, a2 Setting</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_8_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.8. Additional Axis a3 Setting</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_9_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.9. Additional Axis a4 Setting</p></em>
</p>   
</br>

7. Navigate to `System > 5: Initialization > 6: Mechanism Settings` to configure the mechanism for jogging the positioner by each station.  

<!-- ![](../_assets/2_1_10.png) -->
<p align="center">
 <img src="../_assets/2_1_10_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.10. Mechanism Setting</p></em>
</p>   
</br>


8. Power cycle the controller to apply the additional axis, station, and mechanism settings correctly.


[__SOURCE](2-system_settings/2-2-robot-calibration.md)
# 2.2 Robot Calibration

Please refer to the following: [${cont_model} Controller Operation Manual 7.7 Auto Calibration](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/7-system/7-auto-calibration/README?cont_model=${cont_model})
[__SOURCE](2-system_settings/2-3-positioner-calibration/README.md)
# 2.3 Positioner Calibration

- Positioner calibration is a function that automatically calculates the position and movement direction of the positioner using the robot's TCP pose. Therefore, to obtain accurate results from positioner calibration, the robot's TCP pose must be input precisely. As a preliminary step, the "`System > 6: Auto Calibration > Optimize axis origin and tool length`" function can be utilized.

- To use positioner calibration, a group number must be assigned to the positioner axis. A positioner group can consist of up to 2-axes, which can be configured as either rotary-rotary or linear-linear.

- The basic principle of positioner calibration is that, for positioners composed of rotary axes, the positions of three taught points are used to form a circle to calculate the position of the rotation axis.
  Therefore, three taught points per axis are required to calculate the center of each rotary axis.
  In the case of a two-axis positioner with rotary axes, a common middle point is used, totaling five taught points, to calculate the position and direction of each rotation axis.
  For positioners composed of linear axes, since only the axis direction is calculated, two taught points per axis are required.
  For a two-axis linear positioner, the middle point is shared, and the direction of each axis is calculated from three taught points.

- After program teaching, positioner calibration can be performed from the settings screen or by executing the ```posi_calib``` procedure.

[__SOURCE](2-system_settings/2-3-positioner-calibration/1_1axis-positioner-calibration-teaching.md)
# 2.3.1 Teaching the 1-Axis Positioner Calibration Program

1. Select the program to be taught.

2. For a 1-Axis positioner, fix a pointed teaching point on the positioner. It is important to place this teaching point as far as possible from the rotation center to improve callibration accuracy.

3. Rotate the positioner approximately 30° in one direction and precisely teach three points to record the program. The teaching method is illustrated in the figure below.
  For a linear positioner, teach two points as far apart as possible using the same method.

4. When teaching, try to keep the robot's pose consistent.

<!-- ![](../../_assets/image9.png) -->

<p align="center">
 <img src="../../_assets/2_3_1.png"></img>
 <em><p align="center">Figure 2.3.1. Teaching the 1-Axis Positioner Calibration</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/2_2axis-positioner-calibration-teaching.md)
# 2.3.2 Teaching the 2-Axis Positioner Calibration Program


1. Select the program to be taught.

2. Place the pointed teaching point as far as possible from the rotation center.

3. For a 2-axis positioner, similar to the 1-axis positioner, first move only the 2-Axis and teach three points.
  Then, from the 3rd teaching point(S3), move only the 1-Axis to teach the 4th(S4) and 5th(S5) points.
  For a linear positioner, teach two points on the 2-Axis, then move the 1-Axis and teach one point.

4. When teaching, try to keep the robot's pose consistent.

<!-- ![](../../_assets/image10.png) -->

<p align="center">
 <img src="../../_assets/2_3_2.png" width="70%"></img>
 <em><p align="center">Figure 2.3.2. Teaching the 2-Axis Positioner Calibration</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/3_positioner-calibration-execution.md)
# 2.3.3 Executing Positioner Calibration

1. Enter the `System > 4: Application parameters > 3: Positioner synchronization`.
2. Select the station to be calibrated and click the calibration button to enter the taught program number.

<!-- ![](../../_assets/image11.png) -->
<p align="center">
 <img src="../../_assets/2_3_3_en.png" width="60%"></img>
 <em><p align="center">Figure 2.3.3. Executing Positioner Calibration</p></em>
</p>   
</br>

3. The calibration results will be displayed. Press the `[OK]` button on the right to finalize the data settings.

<!-- ![](../../_assets/image12.png) -->
<p align="center">
 <img src="../../_assets/2_3_4_en.png" width="60%"></img>
 <em><p align="center">Figure 2.3.4. Positioner Calibration Result</p></em>
</p>   
</br>

4. If the user knows the exact position of the positioner from CAD data, the position and DH parameters of the positioner can be manually set. Pressing the `[OK]` button will apply the data settings accordingly.

5. You can verify whether the calibration was performed correctly at the following link: [`3.2 Positioner Synchronized Jog Mode`](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/en/3-manual-operation/3-2-positioner-sync-jog-mode?cont_model=${cont_model})

[__SOURCE](2-system_settings/2-3-positioner-calibration/4_posi_calib.md)
# 2.3.4 posi_calib

This command performs the positioner calibration required for the positioner to operate synchronously with the robot.


### Description

Generally, positioner calibration is performed through the settings dialog. However, when the positioner is changed due to a servo tool change, calibration must be updated during robot operation. This command is used to perform calibration within the robot program.

You can verify whether the calibration was performed correctly at the following link: [3.2 Positioner Synchronized Jog Mode](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/en/3-manual-operation/3-2-positioner-sync-jog-mode?cont_model=${cont_model})


### Syntax

```python
posi_calib job=<calibration prog. no.>,s_=<station no.>
```

### Parameters
<table>
  <thead>
    <tr>
      <th style="text-align:left">Item</th>
      <th style="text-align:left">Meaning</th>
      <th style="text-align:left">Remarks</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Calibration Program Number</td>
      <td style="text-align:left">
        Positioner calibration program number
        (1 ~ 9999)
      </td>
      <td style="text-align:left">Variable</td>
    </tr>
    <tr>
      <td style="text-align:left">Station Number</td>
      <td style="text-align:left">
        Station number to be calibrated
      <td style="text-align:left">Variable</td>
    </tr>
  </tbody>
</table>


### Example
```python
          # Program for positioner calibration (9995.job)
     S1   move P,spd=100%,accu=1,tool=0 # Teaching for positioner calibration
     S2   move P,spd=100%,accu=1,tool=0 # Teaching for positioner calibration
     S3   move P,spd=100%,accu=1,tool=0 # Teaching for positioner calibration
```
```python
          # Tool change + positioner calibration
     S1   move P,spd=100%,accu=1,tool=0 
          toolchng on,tg=P1,di=1        # Tool change
          posi_calib job=9995,s_=1      # Positioner calibration
```

[__SOURCE](3-manual-operation/README.md)
# 3. Manual Operation

There are two ways to jog the positioner:  <br/>
- Independent Jog: Jogging the positioner alone.
- Synchronized Jog: Jogging the positioner while the robot moves synchronously to follow it.
[__SOURCE](3-manual-operation/3-1-positioner-independent-jog-mode.md)
# 3.1 Positioner Independent Jog Mode

The independent jog mode is toggled by pressing the "mech." key on the teach pendant. When set to this mode, the positioner can be jogged independently as shown below.

<!-- ![](../_assets/image13.png) -->
<p align="center">
 <img src="../_assets/3_1_1_en.png" width="60%"></img>
 <em><p align="center">Figure 3.1.1. Positioner Independent Jog method</p></em>
</p>   
</br>

- Positioner mechanism: J7 + J8
- Coordinate system: Axis coordinate system (independent jog)
- Recording condition: General move command

[__SOURCE](3-manual-operation/3-2-positioner-sync-jog-mode.md)
# 3.2 Positioner Synchronized Jog Mode

The positioner synchronized jog mode is available only after positioner calibration is completed.
While in the positioner independent jog mode, pressing the "crd.sys" button on the teach pendant will display "Synchronized S1". In this mode, when the positioner moves, the robot follows the positioner's movement and performs synchronized jogging.

<!-- ![](../_assets/image14.png) -->
<p align="center">
 <img src="../_assets/3_1_2_en.png" width="60%"></img>
 <em><p align="center">Figure 3.1.2. Positioner Synchronized Jog Method</p></em>
</p>   
</br>

- Positioner mechanism: J7 + J8
- Coordinate system: Synchronized coordinate system (synchronized jog)
- Recording condition: smov command

<!-- ![](../_assets/image14-1.png) -->
<p align="center">
 <img src="../_assets/3_1_3.png" width="60%"></img>
 <em><p align="center">Figure 3.1.3. Positioner Operation Simulation</p></em>
</p>   
</br>

[__SOURCE](4-program-creation/README.md)
# 4. Programming

[__SOURCE](4-program-creation/4-1-step-recording.md)
# 4.1 Step Recording

- In positioner independent jog mode, the program recording condition is set to the move command.
- In positioner synchronized jog mode, the recording condition is set to the smov command to support positioner synchronized commands.


[__SOURCE](4-program-creation/4-2-smov.md)
# 4.2 smov

```py
	smov {station number}, {interpolation method}, {speed}, {accuracy}, {tool number}
```

- The settings of the smov command are determined within the positioner coordinate system.
  For example, when moving two points in a straight line with the positioner moving, the speed refers to the TCP's movement speed relative to the positioner.

1. Station number: Refers to the positioner group number (S1 ~ S4).
2. Interpolation method: Linear(L) or circular(C) interpolation can be performed on the workpiece.
3. Speed: Sets the speed at which the robot's TCP moves over the workpiece.
4. Accuracy: Sets the accuracy for linear and circular interpolation over the workpiece.
5. Tool number: Sets the robot tool number used for the operation.

[__SOURCE](4-program-creation/4-3-positioner-linear-interpolation-example.md)
# 4.3 Example of Teaching Linear Interpolation on the Positioner

1. Determine the start and target points on the workpiece.

<!-- ![](../_assets/image15.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_1.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.1. Step 1
  </em>
</p>
<br/>

2. Using the Mechanism keys and Coordinate System, select the positioner and move it. Then, switch back to the robot using the Mechanism key and align the robot tool tip to the desired start point. In this state, press the "기록(record)" key to record a move command (use smov if necessary).

3. Use the Mechanism key and Coordinate System to set the mode to positioner synchronized jog. If the positioner being used is Station 1, select the coordinate system as "sync. S1".

<!-- ![](../_assets/image16.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_2.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.2. Step 2~3
  </em>
</p>
<br/>

4. While the master is selected, if you move the positioner to the desired position, the robot will maintain its position and orientation relative to the working start point on the positioner.

<!-- ![](../_assets/image17.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_3.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.3. Step 4
  </em>
</p>
<br/>

5. (Note) The error between a point on the positioner and the robot tool tip in this state is due to calibration errors between the robot and positioner. However, this error does not appear as a trajectory error during playback. In other words, even if some error exists, moving the robot again to the target position and recording with smov will result in minimal trajectory position errors during playback.

6. Switch the mechanism back to the robot, then use the jog key to move the robot to the target point (S2) and align it.

<!-- ![](../_assets/image18.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_4.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.4. Step 6
  </em>
</p>
<br/>

7. To record the synchronized step (smov), set the mode back to positioner synchronized jog and select the coordinate system as Synchronized S1, then press the "기록(record)" key to record the smov step.

8. Follow steps ③→④→⑤ for subsequent steps.

<!-- ![](../_assets/image19.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_5.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.5. Step 7~8
  </em>
</p>
<br/>


9. When the recorded program is executed, the positioner moves and the robot performs linear interpolation relative to the workpiece on the positioner.

<!-- ![](../_assets/image20.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_6.png" width="50%" style="display: block;" />
  <em style="display: block; text-align: center; width: 50%; auto;">
    Figure 4.1.6. Step 9
  </em>
</p>
<br/>


`Caution`
1) Recording positioner synchronized steps (smov) does not necessarily have to follow the exact method described above.
  You can move the robot and positioner independently to set the position and orientation, then record the step as smov.
  The robot will move according to the specified interpolation method relative to the workpiece on the positioner.

2) If two consecutive smov steps both use linear interpolation ("L"), cornering motion will be performed just like with move commands.

3) The speed set in smov steps is the working speed.
  Therefore, even if the positioner moves a lot, if the working distance between recorded steps on the workpiece is very short, the positioner's working speed may effectively become infinite(∞), causing it to move at its maximum speed.
  To limit the positioner speed in such cases, set the speed unit to "SEC".
  This means the step movement is based on time, not speed, so even if the distance on the workpiece is zero(0), the move time is specified.
<br/><br/>


`Example of Programming`
```py

    S1   move  L,spd=60%,accu=1,tool=0        # Approach start position step
    S2   smov  S1,L,spd=100mm/s,accu=1,tool=0    # Positioner synchronized linear interpolation
    S3   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S4   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S5   move  P,spd=10%,accu=1,tool=0        # Retract step (asynchronous with positioner)
    S6   move  L,spd=200mm/s,accu=1,tool=0 
    end

```

[__SOURCE](5-add-axis-move-independent-execution/README.md)
# 5. Independent Execution of Additional Axis Movement


The Independent Additional Axis Movement function enables the additional axis to execute move commands independently from the robot in response to external input signals.
[__SOURCE](5-add-axis-move-independent-execution/5-1-system-setting.md)
# 5.1 System Settings

1. Navigate to the `System - Application Parameter - Command Independent execution`.  
![](../_assets/5_1_1_en.png)  
    - Input Signal  
    Configure the signal input to the controller.

    - Command  
    Specify the command to be executed when the input signal changes from OFF to ON. For independent operation of the positioner, a move command is used.  

    - Ouput Singal under Execution  
    This signal turns On when execution of the specified command starts and turns OFF when execution is completed.  

    - Output Signal After Execution Completed  
    This signal turns OFF when execution of the specified command starts and turns ON when execution is completed.  
    For more details on Independent Command Execution, refer to [${cont_model} Controller Operation Manual - 7.5.10 Command independent execution](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/7-system/5-application-parameter/10-cmd-idp-exe?cont_model=${cont_model}).  
  
2. In the Command field, press the button below to enter a move command. To execute an additional axis move independently, the mechanism must be specified in the move command.  
    For more details on entering move commands, refer to [${cont_model} Controller Operation Manual - Robot Language HRScript - 5.1 Pose](https://hrbook-hrc.web.app/#/view/doc-hrscript/en/5-moving-robot/1-pose?cont_model=${cont_model}).  

3. Set the axis to be operated independently using the axisctrl off command. The axisctrl command is used to select whether an additional axis is controlled by the task program. An axis set to axisctrl off does not move to the positions recorded in the task program and can be moved independently. An axis set to axisctrl on moves according to the positions recorded in the task program.  
    Independent execution of move commands by external input signals is valid only in the section between axisctrl off and axisctrl on. When an input signal specified in Independent Command Execution is received while axisctrl off is active, the move command is executed. Axes set to axisctrl off are displayed in yellow text, such as j_7 shown at the top of the figure below.  
    ![](../_assets/5_1_2_en.png)  
    For more details, refer to [${cont_model} Controller Manual - Multi-tasking - 2.1.6 axisctrl](https://hrbook-hrc.web.app/#/view/doc-multi-task/en/2-related-function/2-1-command-sentence/6-axisctrl?cont_model=${cont_model}).  


{% hint style="warning" %}  

1. The mechanism specified in the move command for Independent Command Execution must consist only of axes set to axisctrl off.

2. If the axisctrl on command is executed before the independent execution is completed, the error **'E1455 (Axis 0) Independent operation not completed'** occurs and the robot axes are stopped. In this case, the independently operated axis continues moving to its target position.  

    This occurs because the execution time of the robot task program is shorter than the execution time of the independent move command. Modify the program accordingly, or insert a wait command before the axisctrl on command to check whether the independent execution completion signal has been output.

{% endhint %}

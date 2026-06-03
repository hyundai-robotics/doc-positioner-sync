# 4.3 Example of Teaching Linear Interpolation on the Positioner

1. Determine the start and target points on the workpiece.

<p style="text-align: left;">
  <img src="../_assets/4_1_1.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.1. Step 1
  </em>
</p>
<br/>

2. Using the Mechanism keys and Coordinate System, select the positioner and move it. Then, switch back to the robot using the Mechanism key and align the robot tool tip to the desired start point. In this state, press the "기록(record)" key to record a move command (use smov if necessary).

3. Use the Mechanism key and Coordinate System to set the mode to positioner synchronized jog. If the positioner being used is Station 1, select the coordinate system as "sync. S1".

<p style="text-align: left;">
  <img src="../_assets/4_1_2.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.2. Step 2~3
  </em>
</p>
<br/>

4. While the master is selected, if you move the positioner to the desired position, the robot will maintain its position and orientation relative to the working start point on the positioner.

<p style="text-align: left;">
  <img src="../_assets/4_1_3.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.3. Step 4
  </em>
</p>
<br/>

5. (Note) The error between a point on the positioner and the robot tool tip in this state is due to calibration errors between the robot and positioner. However, this error does not appear as a trajectory error during playback. In other words, even if some error exists, moving the robot again to the target position and recording with smov will result in minimal trajectory position errors during playback.

6. Switch the mechanism back to the robot, then use the jog key to move the robot to the target point (S2) and align it.

<p style="text-align: left;">
  <img src="../_assets/4_1_4.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.4. Step 6
  </em>
</p>
<br/>

7. To record the synchronized step (smov), set the mode back to positioner synchronized jog and select the coordinate system as Synchronized S1, then press the "REC(record)" key to record the smov step.

8. Follow steps ③→④→⑤ for subsequent steps.

<p style="text-align: left;">
  <img src="../_assets/4_1_5.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    Figure 4.1.5. Step 7~8
  </em>
</p>
<br/>


9. When the recorded program is executed, the positioner moves and the robot performs linear interpolation relative to the workpiece on the positioner.

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

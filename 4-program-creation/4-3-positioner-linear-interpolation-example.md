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
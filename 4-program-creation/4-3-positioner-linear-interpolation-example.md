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

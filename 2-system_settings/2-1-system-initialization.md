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

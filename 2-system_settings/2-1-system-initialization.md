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
  Once the robot type is selected, the screen shown bellow will apper. Enter the total number of auxiliary axes to be used. After completing the settings, press the Confirm button.

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
</br>

4. After the controller boots up, navigate to `System > 5: Initialization > 5: Additional axis parameter setting` to configure the auxiliary axes.
  On this screen, set the auxiliary axes corresponding to positioners by selecting the axis specification as "Positioner" and configure the relevant parameters.
  Depending on the configuration of the positioner axis, select either linear or rotary axis.
  For linear axis, if the operating direction of the positioner axis is known relative to the robot base coordinates, specify the direction accordingly. If the exact direction is unknown, select arbitrarily.
  For rotary axis, if the positioner is not a standard one provided by the manufacturer, set the axis configuration to "Custom" and configure the remaining parameters.
  For detailed instructions on configuring auxiliary axes, please refer to the [Auxiliary Axis Function User Manual](https://hrbook-hrc.web.app/#/view/doc-add-axes/en/README?cont_model=${cont_model}).


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
  Select each station and enter the auxiliary axis number to configure the station. For 1-axis positioners, enter the auxiliary axis number only in the first field.
  In the figure below, auxiliary axes a1 and a2 correspond to the 2-axis positioner at Station 1, a3 corresponds to the 1-axis positioner at Station 2, and a4 corresponds to the 1-axis positioner at Station 3.

<!-- ![](../_assets/2_1_7.png)  
![](../_assets/2_1_8.png)  
![](../_assets/2_1_9.png)   -->
<p align="center">
 <img src="../_assets/2_1_7_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.7. Auxiliary Axis a1, a2 Setting</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_8_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.8. Auxiliary Axis a3 Setting</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_9_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.9. Auxiliary Axis a4 Setting</p></em>
</p>   
</br>

7. Navigate to `System > 5: Initialization > 6: Mechanism Settings` to configure the mechanism for jogging the positioner by each station.  

<!-- ![](../_assets/2_1_10.png) -->
<p align="center">
 <img src="../_assets/2_1_10_en.png" width="60%"></img>
 <em><p align="center">Figure 2.1.10. Mechanism Setting</p></em>
</p>   
</br>


8. Power cycle the controller to apply the auxiliary axis, station, and mechanism settings correctly.


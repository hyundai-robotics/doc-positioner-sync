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
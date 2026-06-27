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
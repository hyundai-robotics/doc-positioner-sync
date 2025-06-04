# 2.3.4 posi_calib

This command performs the positioner calibration required for the positioner to operate synchronously with the robot.


### Description

Generally, positioner calibration is performed through the settings dialog. However, when the positioner is changed due to a servo tool change, calibration must be updated during robot operation. This command is used to perform calibration within the robot program.

You can verify whether the calibration was performed correctly at the following link: [**3.2장 포지셔너 동기 조그 모드**](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/korean/3-manual-operation/3-2-positioner-sync-jog-mode)


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

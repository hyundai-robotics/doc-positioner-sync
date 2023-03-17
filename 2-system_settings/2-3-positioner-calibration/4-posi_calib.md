# 2.3.4 posi_calib
포지셔너가 로봇과 동기동작을 하기 위해 필요한 포지셔너 캘리브레이션을 수행하는 명령입니다. 

### 설명
일반적으로 포지셔너 캘리브레이션은 설정 대화상자를 통해 수행합니다. 그러나, 서보툴 체인지로 포지셔너가 변경되는 경우에는 로봇 운전 중 캘리브레이션이 변경되어야 합니다. 이를 로봇 프로그램 상에서 수행하기 위한 명령입니다. 

[**3.2장 포지셔너 동기 조그 모드**](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/korean/3-manual-operation/3-2-positioner-sync-jog-mode)에서 캘리브레이션이 정상적으로 수행되었는지 확인할 수 있습니다.

### 문법

```python
posi_calib job=<캘리브레이션 프로그램 번호>,s_=<스테이션 번호>
```

### 파라미터
<table>
  <thead>
    <tr>
      <th style="text-align:left">항목</th>
      <th style="text-align:left">의미</th>
      <th style="text-align:left">기타</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">캘리브레이션 프로그램 번호</td>
      <td style="text-align:left">
        포지셔너 캘리브레이션 프로그램 번호
        (1 ~ 9999)
      </td>
      <td style="text-align:left">변수</td>
    </tr>
    <tr>
      <td style="text-align:left">스테이션 번호</td>
      <td style="text-align:left">
        캘리브레이션 할 스테이션 번호
      <td style="text-align:left">변수</td>
    </tr>
  </tbody>
</table>

```python
          # 포지셔너 캘리브레이션용 프로그램(9995.job)
     S1   move P,spd=100%,accu=1,tool=0 # 포지셔너 캘리브레이션 교시
     S2   move P,spd=100%,accu=1,tool=0 # 포지셔너 캘리브레이션 교시
     S3   move P,spd=100%,accu=1,tool=0 # 포지셔너 캘리브레이션 교시
```
```python
          # 툴체인지 + 포지셔너 캘리브레이션
     S1   move P,spd=100%,accu=1,tool=0 
          toolchng on,tg=P1,di=1        # 툴체인지
          posi_calib job=9995,s_=1      # 포지셔너 캘리브레이션
```

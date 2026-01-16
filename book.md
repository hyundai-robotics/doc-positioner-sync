
[__SOURCE](README.md)
# ${cont_model} 제어기 기능설명서 - 포지셔너 동기

[__SOURCE](1-intro/README.md)
# 1. 개요

포지셔너(positioner) 동기 기능은 로봇 외부에 설치된 지그 장치 동작에 동기화하여 로봇이 추종하거나 그 지그장치에 대해 상대적인 직선 혹은 원호 동작을 가능하게 하는 기능입니다. 포지셔너 동기 기능에 적용되는 외부 지그 장치를 포지셔너라고 칭하며, 스테이션(station)이라고도 합니다. 

본 기능을 적용하면 로봇의 작업영역의 제한으로 인해 작업이 어려운 부분을 보완할 수 있습니다. 즉, 작업물이 포지셔너 위에 고정되어 있는 상태에서 포지셔너가 이동하더라도 로봇은 이 포지셔너의 움직임을 추종하면서 작업물 위에서 직선 또는 원호의 동작을 수행하게 됩니다.  

주요 기능 사양은 아래와 같습니다.
|   **주요 기능 사양**  | **특징**                            |
|   -                   | -                                  |
|    포지셔너 그룹      | 1~4 그룹 지원                        |
|    포지셔너 축 수     | 1축, 2축 포지셔너 지원(회전축, 직동축) |
|    보간 방식          | 직선, 원호 보간 지원                  |
|    외부입력 독립재생   | 자동모드에서 로봇과 무관하게 포지셔너 독립재생(move) 기능 지원  |

<br/><br/>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="../_assets/1_0_1.png" alt="1축 회전 포지셔너" width="100%" />
      <br />
      <em>그림 1.0.1. 1축 회전 포지셔너</em>
    </td>
    <td align="center" width="50%">
      <img src="../_assets/1_0_2.png" alt="2축 회전 포지셔너" width="100%" />
      <br />
      <em>그림 1.0.2. 2축 회전 포지셔너</em>
    </td>
  </tr>
</table>

<!-- 
| <img src="../_assets/1_0_1.png" height="447px" width="357px"> | <img src="../_assets/1_0_2.png" height="447px" width="357px"> |
|:-: | :-:|             
|1축 회전 포지셔너|  2축 회전 포지셔너   |
 -->

[__SOURCE](1-intro/1-1-major-functions.md)
# 1.1 주요 기능

#### 멀티 그룹 포지셔너(Multi-group Positioner)  
부가축으로 설정한 지그축(Jig)을 포지셔너 그룹으로 설정하여 제어합니다. 총 3그룹의 포지셔너를 등록할 수 있으며, 각 그룹은 2축 포지셔너까지 설정이 가능합니다.

#### 포지셔너 캘리브레이션  
포지셔너의 좌표계를 설정하기 위해 회전축으로 구성된 1축 포지셔너의 경우는 3점, 2축 포지셔너의 경우에는 5점 직동축인 경우는 1축 직동 포지셔너의 경우 2점, 2축 직동 포지셔너의 경우 5점의 교시를 통하여 포지셔너의 캘리브레이션이 수행됩니다.

#### 교시

포지셔너 독립조작 기능의 교시는 보조축 키의 선택에 의해 로봇 직교 좌표계, 포지셔너 동기 조그, 부가축 조작 등으로 전환되어 사용하도록 설계 되어 있어 포지셔너 동기 동작 명령(smov)를 교시하는데 편리합니다.

#### 재생

포지셔너 동기기능은 직선 보간, 원호 보간을 모두 지원합니다. 동기 동작명령(smov) 명령이 실행되면 포지셔너 위에서 보간 동작을 실행하며 재생됩니다. 


#### 부가축 독립 move 기능

외부신호를 이용하여 별도로 등록된 move 명령어를 자동모드에서 구동하는 기능입니다. 이 기능을 사용하면 로봇의 동작과 독립적인 부가축 동작을 move 명령어를 이용하여 구현이 가능합니다. 이 기능을 사용하기 위해서는 메커니즘 설정과 명령문 독립실행 설정이 필요합니다.
[__SOURCE](1-intro/1-2-operation-sequence.md)
# 1.2 조작 순서


<p align="center">
 <img src="../_assets/1_2_1.png" width="60%"></img>
 <em><p align="center">그림 1.2.1. 조작 순서</p></em>
</p>   
</br>

[__SOURCE](2-system_settings/README.md)
# 2. 시스템 설정
[__SOURCE](2-system_settings/2-1-system-initialization.md)
# 2.1 시스템 초기화

1. 제어기를 처음으로 설정하는 경우에는 시스템 초기화를 수행합니다.
  `시스템 > 초기화 > 시스템 초기화`를 선택하고 초기화 버튼을 누릅니다.

<!-- ![](../_assets/2_1_1.png) -->
<p align="center">
 <img src="../_assets/2_1_1.png" width="60%"></img>
 <em><p align="center">그림 2.1.1. 시스템 초기화</p></em>
</p>   
</br>


2. 시스템 초기화 이후에는 로봇 타입을 선택합니다.
  로봇 타입을 선택하면 다음 화면이 나타납니다. 이때 사용할 총 부가축의 개수를 입력합니다. 설정이 완료되면 확인 버튼을 누릅니다.  

<p align="center">
 <img src="../_assets/2_1_2.png" width="60%"></img>
 <em><p align="center">그림 2.1.2. 로봇 타입 선택</p></em>
</p>   
</br>

<!-- ![](../_assets/2_1_2.png)
![](../_assets/2_1_3.png) -->

3. 제어기 전원을 재투입합니다.  

<p align="center">
 <img src="../_assets/2_1_3.png" width="60%"></img>
 <em><p align="center">그림 2.1.3. 재부팅</p></em>
</p>   
</br>

4. 제어기 부팅이 완료된 후 `시스템 > 초기화 > 부가축 파라미터 설정` 메뉴에 진입해 부가축을 설정합니다.
  이 화면에서 포지셔너에 해당하는 부가축은 축 사양을 포지셔너로 설정하고 해당하는 파라미터를 설정합니다. 포지셔너 축의 구성 형태에 따라 직동 또는 회전 축을 선택 하십시오. 직동 축인 경우 로봇 베이스 좌표 기준으로 포지셔너 축의 동작 방향을 알고 있는 경우 방향을 지정 할 수 있습니다. 정확한 방향을 알수 없는 경우 임의로 선택 하십시오. 회전 축의 경우 당사가 제공하는 표준 포지셔너가 아닌 경우에는 축 구성을 '임의'로 설정하고 나머지 파라미터를 설정합니다. 부가축 파라미터 설정 방법은 [부가축 기능 사용설명서](https://hrbook-hrc.web.app/#/view/doc-add-axes/ko/README?cont_model=${cont_model}) 를 참고하십시오.

<!-- ![](../_assets/2_1_4.png)
![](../_assets/2_1_5.png) -->
<p align="center">
 <img src="../_assets/2_1_4.png" width="60%"></img>
 <em><p align="center">그림 2.1.4. 직동 축 파리미터 구성</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_5.png" width="60%"></img>
 <em><p align="center">그림 2.1.5. 회전 축 파라미터 구성</p></em>
</p>   
</br>

5. 만약 당사에서 제공하는 포지셔너인 경우에는 축 구성에서 해당 목록을 선택하십시오.
  이 경우에는 다른 파라미터를 설정할 필요가 없습니다.

<p align="center">
 <img src="../_assets/2_1_6.png" width="60%"></img>
 <em><p align="center">그림 2.1.6. 당시 포지셔너 구성</p></em>
</p>   
</br>

<!-- ![](../_assets/2_1_6.png) -->

6. `시스템 > 응용 파라미터 > 포지셔너 동기`메뉴에서 포지셔너 그룹을 설정합니다. 
2축 포지셔너 1개, 1축 포지셔너 2개를 설정하는 경우를 예시로 들겠습니다. 
스테이션이 3개 필요하므로 스테이션을 추가해야 합니다. '+'버튼을 누르면 리스트 창에 스테이션이 생성됩니다.
각 스테이션을 선택하고 부가축 번호를 입력하여 스테이션을 설정합니다. 1축 포지셔너의 경우 첫번째 칸에만 부가축 번호를 입력합니다.
아래 그림에서는 부가축 a1, a2축은 2축 포지셔너로 스테이션 1이고 a3축은 1축 포지셔너로 스테이션 2, 마지막으로 a4축은 1축 포지셔너로써 스테이션 3으로 설정한 경우입니다.

<!-- ![](../_assets/2_1_7.png)  
![](../_assets/2_1_8.png)  
![](../_assets/2_1_9.png)   -->
<p align="center">
 <img src="../_assets/2_1_7.png" width="60%"></img>
 <em><p align="center">그림 2.1.7. 부가축 a1, a2 설정</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_8.png" width="60%"></img>
 <em><p align="center">그림 2.1.8. 부가축 a3 설정</p></em>
</p>   
</br>
<p align="center">
 <img src="../_assets/2_1_9.png" width="60%"></img>
 <em><p align="center">그림 2.1.9. 부가축 a4 설정</p></em>
</p>   
</br>


7. `시스템 > 초기화 > 메커니즘 설정`메뉴에서 포지셔너를 스테이션별로 조그하기 위해 메커니즘을 설정합니다.

<!-- ![](../_assets/2_1_10.png) -->
<p align="center">
 <img src="../_assets/2_1_10.png" width="60%"></img>
 <em><p align="center">그림 2.1.10. 매커니즘 설정</p></em>
</p>   
</br>


8. 제어기 전원을 재투입하면 부가축, 스테이션, 메커니즘 설정이 정상적으로 적용됩니다.
[__SOURCE](2-system_settings/2-2-robot-calibration.md)
# 2.2 로봇 캘리브레이션

[**${cont_model} 제어기 조작설명서 7.7장 자동 캘리브레이션**](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/ko-tp630/7-setting/7-auto-calibration/README?cont_model=${cont_model})을 참고하십시오.
[__SOURCE](2-system_settings/2-3-positioner-calibration/README.md)
# 2.3 포지셔너 캘리브레이션
  
- 포지셔너 캘리브레이션은 로봇의 TCP 위치를 이용하여 포지셔너의 위치와 동작 방향에 대한 정보를 자동으로 계산하는 기능 입니다. 따라서, 포지셔너 캘리브레이션을 수행하기 위해서 로봇의 TCP 위치가 정확하게 입력되어 있어야 정확한 결과를 얻을 수 있습니다. 이를 위한 사전 작업으로 "축원점 및 툴길이 최적화" 기능을 활용할 수 있습니다. 

- 포지셔너 캘리브레이션을 사용하기 위해서는 포지셔너축에 대해서 그룹번호가 지정되어 있어야 합니다. 포지셔너 그룹은 최대 2축으로 구성 가능하며 회전-회전 또는 직동-직동 으로 구성될 수 있습니다. 

- 포지셔너 캘리브레이션의 기본적인 원리는 포지셔너가 회전 축으로 구성된 경우 교시된 3점의 위치로부터 원을 구성하여 회전축의 위치를 계산하는 방식입니다. 따라서 회전축의 중심을 계산하기 위해서는 축 별로 3점의 교시점이 필요합니다. 회전축으로 구성된 2축 포지셔너의 경우 가운데 한 점을 공통으로 활용하여 총 5점의 교시점을 활용하여 각각의 회전축의 위치와 방향을 계산 할 수 있습니다. 직동축으로 구성된 포지셔너의 경우는 포지셔너의 축 방향만을 계산하기 때문에 축별로 2점의 교시점이 필요하며, 2축으로 구성된 경우에는 가운데 점을 공통으로 활용하여 총 3점의 교시점으로부터 각각의 축 동작 방향을 계산하게 됩니다. 

- 프로그램 교시 후 설정화면에서 수행하거나 posi_calib 프로시져를 통해 포지셔너 캘리브레이션을 계산할 수 있습니다.
[__SOURCE](2-system_settings/2-3-positioner-calibration/1_1axis-positioner-calibration-teaching.md)
# 2.3.1 1축 포지셔너 캘리브레이션 프로그램 교시

1.	교시할 프로그램을 선택합니다.
2.	1축 포지셔너의 경우에는 포지셔너 위에 뾰족한 티칭점을 고정합니다. 이때 이 티칭점을 가능한 회전 중심과 멀리 설치하여야 캘리브레이션이 정확합니다.
3.	포지셔너를 30°정도씩 한 방향으로 회전시키면서 3점을 정확히 티칭하여 프로그램을 기록합니다. 티칭하는 방법은 아래의 그림과 같습니다.
직동 포지셔너의 경우는 가능한 멀리 떨어진 2점을 상기와 같은 방법으로 교시 합니다. 
4.	교시할 때 로봇의 자세는 가능하면 동일하게 합니다.

<!-- ![](../../_assets/image9.png) -->

<p align="center">
 <img src="../../_assets/2_3_1.png" width="70%"></img>
 <em><p align="center">그림 2.3.1. 1축 포지셔너 캘리브레이션 교시 방법</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/2_2axis-positioner-calibration-teaching.md)
# 2.3.2 2축 포지셔너 캘리브레이션 프로그램 교시

1.	교시할 프로그램을 선택합니다.
2.	뾰족한 티칭점을 가능한 회전 중심과 멀리 설치합니다.
3.	2축 포지셔너의 경우에는 1축 포지셔너와 마찬가지로 두번째 축만 움직여 3점을 우선 교시합니다. 이 후에 3번째 교시점(S3)에서 첫번째 축만 이동하여 4번째 점과(S4) 5번째 점을(S5) 교시합니다. 직동 포지셔너의 경우 두번째 축에 대해 2점 교시 후 첫번째 축에 대해 이동 후 한점을 교시합니다. 
4.	교시를 할 때에는 로봇의 자세는 가능하면 변경하지 않고 교시하면 정확한 캘리브레이션이 됩니다.

<!-- ![](../../_assets/image10.png) -->

<p align="center">
 <img src="../../_assets/2_3_2.png" width="70%"></img>
 <em><p align="center">그림 2.3.2. 2축 포지셔너 캘리브레이션 교시 방법</p></em>
</p>   
</br>
[__SOURCE](2-system_settings/2-3-positioner-calibration/3_positioner-calibration-execution.md)
# 2.3.3 포지셔너 캘리브레이션 실행

1. `시스템 > 응용 파라미터 > 포지셔너 동기`로 진입합니다.
2. 캘리브레이션 할 스테이션을 선택하고 캘리브레이션 버튼을 클릭하여 교시한 작업 프로그램 번호를 입력 합니다.

<!-- ![](../../_assets/image11.png) -->
<p align="center">
 <img src="../../_assets/2_3_3.png" width="60%"></img>
 <em><p align="center">그림 2.3.3. 포지셔너 캘리브레이션 실행</p></em>
</p>   
</br>

3. 캘리브레이션 결과가 표시됩니다. 우측의 『확인』키를 누르면 해당 데이터 설정이 완료됩니다. 

<!-- ![](../../_assets/image12.png) -->
<p align="center">
 <img src="../../_assets/2_3_4.png" width="60%"></img>
 <em><p align="center">그림 2.3.4. 포지셔너 캘리브레이션 결과</p></em>
</p>   
</br>

4. 사용자가 캐드데이터로 포지셔너의 위치를 정확히 알고 있는 경우 수동으로 포지셔너의 위치 및 DH파라미터를 설정한 후 『확인』키를 누르면 마찬가지로 데이터 설정이 반영됩니다.

5. 다음 링크에서 캘리브레이션이 정상적으로 수행되었는지 확인할 수 있습니다. `3.2장 포지셔너 동기 조그 모드`(https://hrbook-hrc.web.app/#/view/doc-positioner-sync/korean/3-manual-operation/3-2-positioner-sync-jog-mode)
[__SOURCE](2-system_settings/2-3-positioner-calibration/4_posi_calib.md)
# 2.3.4 posi_calib
포지셔너가 로봇과 동기동작을 하기 위해 필요한 포지셔너 캘리브레이션을 수행하는 명령입니다. 

### 설명
일반적으로 포지셔너 캘리브레이션은 설정 대화상자를 통해 수행합니다. 그러나, 서보툴 체인지로 포지셔너가 변경되는 경우에는 로봇 운전 중 캘리브레이션이 변경되어야 합니다. 이를 로봇 프로그램 상에서 수행하기 위한 명령입니다. 

[**3.2장 포지셔너 동기 조그 모드**](https://hrbook-hrc.web.app/#/view/doc-positioner-sync/ko/3-manual-operation/3-2-positioner-sync-jog-mode?cont_model=${cont_model})에서 캘리브레이션이 정상적으로 수행되었는지 확인할 수 있습니다.

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


### 사용 예
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

[__SOURCE](3-manual-operation/README.md)
# 3. 수동 조작

포지셔너를 조그하는 방법은 포지셔너만 조그하는 '단독 조그 방법'과 포지셔너를 조그하여 움직였을 때 로봇이 동기화 하여 따라오도록 하는 '동기 조그 방법' 두가지 방법이 있습니다.
[__SOURCE](3-manual-operation/3_1-positioner-independent-jog-mode.md)
# 3.1 포지셔너 단독 조그 모드
단독 조그 방법은 티칭 펜던트의 '메커니즘'키를 누르면 해당 메커니즘으로 토글되어 선택이 변경됩니다. 아래와 같은 상태에서 포지셔너는 단독으로 조그됩니다.

<!-- ![](../_assets/image13.png) -->
<p align="center">
 <img src="../_assets/3_1_1.png" width="60%"></img>
 <em><p align="center">그림 3.1.1. 포지셔너 단독 조그 방법</p></em>
</p>   
</br>


- 포지셔너 메커니즘: J7+J8
- 좌표계: 축 좌표계(단독 조그)
- 기록 조건: 일반 move 명령
[__SOURCE](3-manual-operation/3_2-positioner-sync-jog-mode.md)
# 3.2 포지셔너 동기 조그 모드
포지셔너 동기조그는 포지셔너 캘리브레이션이 완료된 경우에만 사용 가능합니다. 
포지셔너 단독 조그 상태에서, 티칭 펜던트의 '좌표계' 버튼을 누르면 '동기 S1'과 같이 표시됩니다. 이 상태에서 포지셔너를 움직이면 로봇이 포지셔너의 움직임에 따라오면서 조그 동작을 합니다. 

<!-- ![](../_assets/image14.png) -->
<p align="center">
 <img src="../_assets/3_1_2.png" width="60%"></img>
 <em><p align="center">그림 3.1.2. 포지셔너 동기 조그 방법</p></em>
</p>   
</br>

- 포지셔너 메커니즘: J7+J8
- 좌표계: 동기 좌표계(동기 조그)
- 기록 조건: smov 명령

<!-- ![](../_assets/image14-1.png) -->
<p align="center">
 <img src="../_assets/3_1_3.png" width="60%"></img>
 <em><p align="center">그림 3.1.3. 포지셔너 동작 시뮬레이션</p></em>
</p>   
</br>

[__SOURCE](4-program-creation/README.md)
# 4. 프로그램 작성

[__SOURCE](4-program-creation/4-1-step-recording.md)
# 4.1 스텝 기록
- 포지셔너 단독 조그 동작에서는 프로그램 기록 조건이 move 명령으로 설정됩니다. 
- 포지셔너 동기 조그 동작에는 기록조건이 smov 명령으로 설정되어 포지셔너 동기 명령을 지원합니다.

[__SOURCE](4-program-creation/4-2-smov.md)
# 4.2 smov

```py
	smov {스테이션 번호}, {보간방식}, {속도}, {Accuracy}, {Tool 번호}
```

1. 스테이션 번호 : 포지셔너 그룹 번호를 의미합니다. (S1~S4)
2. 보간 방식 : 작업물 상에서 직선(L) 혹은 원호(C) 보간을 할 수 있습니다.
3. 속도 : 작업물 위에서 로봇의 TCP가 이동하는 속도를 설정합니다.
4. Accuracy : 작업물 위에서 직선, 원호 보간의 Accuracy를 설정합니다.
5. Tool 번호 : 작업을 수행하는 로봇 툴 번호를 설정합니다.

- smov 명령의 설정은 포지셔너 좌표계 위에서 결정되는 것입니다. 예를 들어 속도의 경우 포지셔너를 움직이면서 두 점을 직선으로 이동한 경우 포지셔너 위에서 TCP가 이동하는 속도가 설정됩니다.

[__SOURCE](4-program-creation/4-3-positioner-linear-interpolation-example.md)
# 4.3 포지셔너 상의 직선보간 교시 예시

1. 대상물 위에 시작점 및 목표점을 결정합니다.

<!-- ![](../_assets/image15.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_1.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    그림 4.1.1. 과정 1
  </em>
</p>
<br/>

2. 메커니즘 키와 좌표계를 이용하여 포지셔너를 선택하여 포지셔너를 이동시킨 후, 다시 메커니즘키로 로봇을 선택하여 시작점에 로봇 툴 끝을 원하는 시작점에 일치시킵니다. 이 상태에서 기록키를 눌러 'move'명령을 기록합니다(필요에 따라 smov로 기록하십시오).

3. 메커니즘 키와 좌표계 키를 이용하여 포지셔너 동기 조그 모드로 설정합니다. 현재 작업하는 포지셔너가 스테이션 1일 경우 좌표계가 '동기 S1'이 되도록 선택합니다.

<!-- ![](../_assets/image16.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_2.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    그림 4.1.2. 과정 2~3
  </em>
</p>
<br/>

4. 마스터를 선택한 상태에서 포지셔너의 위치를 희망하는 위치로 변경하면, 로봇은 포지셔너 위의 작업 시작점을 따라 자세와 위치가 유지됩니다.

<!-- ![](../_assets/image17.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_3.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    그림 4.1.3. 과정 4
  </em>
</p>
<br/>

5. (참고) 상기 상태에서 포지셔너 위의 한 점과 로봇 툴 끝의 오차는 로봇과 포지셔너의 캘리브레이션에 기인하는 오차이며, 이 오차가 재생시의 궤적오차로 나타나지는 않습니다. 즉, 어느 정도 오차량이 있을 지라도 로봇을 다시 움직여 목표위치로 로봇을 움직이고 "smov"로 기록하면, 재생시의 스텝의 궤적위치 오차는 거의 발생하지 않습니다.

6. 메커니즘을 다시 로봇으로 선택한 다음, Jog키로 로봇을 '목표점'(S2)까지 이동하여 일치시킵니다.

<!-- ![](../_assets/image18.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_4.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    그림 4.1.4. 과정 6
  </em>
</p>
<br/>

7. 동기스텝(smov)을 기록하기 위해 다시 포지셔너 동기 조그 모드로 설정하여 좌표계가 '동기 S1'이 되도록 선택하고 [기록]키를 눌러서 "smov" 스텝을 기록합니다. 

8. 이후의 스텝도 ③→④→⑤의 과정을 따릅니다.

<!-- ![](../_assets/image19.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_5.png" width="40%" style="display: block;" />
  <em style="display: block; text-align: center; width: 40%; auto;">
    그림 4.1.5. 과정 7~8
  </em>
</p>
<br/>


9. 기록된 프로그램을 실행하면, 포지셔너가 이동하고 로봇은 포지셔너 위의 작업물에 대해 직선 보간으로 이동합니다.

<!-- ![](../_assets/image20.png) -->
<p style="text-align: left;">
  <img src="../_assets/4_1_6.png" width="50%" style="display: block;" />
  <em style="display: block; text-align: center; width: 50%; auto;">
    그림 4.1.6. 과정 9
  </em>
</p>
<br/>


`주의사항`
1) 포지셔너 동기스텝(smov)의 기록은 반드시 위와 같은 방법으로 해야하는 것은 아닙니다. 로봇과 포지셔너를 단독으로 움직여 위치와 자세를 결정한 후 smov 스텝으로 기록하면 로봇은 포지셔너의 작업물 위에서 지정된 보간 방식으로 움직입니다.
2) smov 기록된 두 스텝의 보간방식이 둘 다 "L"인 경우 move에서와 같이 코너링 모션을 합니다.
3) smov로 기록된 스텝의 속도는 작업속도입니다. 따라서 포지셔너를 많이 움직였을 지라도 작업물위에 기록된 스텝간의 작업거리가 매우 짧으면 포지셔너이 작업속도가 거의 ∞(무한대)가 되므로 포지셔너가 최고속으로 움직이게 됩니다. 이와 같은 경우 포지셔너의 속도를 제한하고자 할 경우에는 속도 단위를 "SEC"로 설정하면 됩니다. 이 의미는 스텝을 이동하는 단위가 속도가 아닌 시간으로 설정하기 때문에 작업물상의 작업거리가 0일지라도 이동시간이 지정되기 때문입니다.
<br/><br/>
 
`프로그램 작성 예시`
```py

    S1   move  L,spd=60%,accu=1,tool=0		# 시작 위치 접근 스텝
    S2   smov  S1,L,spd=100mm/s,accu=1,tool=0	# 포지셔너 동기 직선 보간
    S3   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S4   smov  S1,L,spd=100mm/s,accu=1,tool=0
    S5   move  P,spd=10%,accu=1,tool=0		# 퇴피 스텝(포지셔너와 비동기)
    S6   move  L,spd=200mm/s,accu=1,tool=0 
    end

```

[__SOURCE](5-add-axis-move-independent-execution/README.md)
# 5. 부가축 move 독립 실행
부가축 move 독립 실행 기능은 외부입력 신호에 의해 부가축의 move 명령을 로봇과 독립적으로 실행할 수 있습니다.
[__SOURCE](5-add-axis-move-independent-execution/5-1-system-setting.md)
# 5.1 시스템 설정
1. `시스템 - 응용 파라미터 - 명령문 독립 실행` 메뉴에 진입합니다.  
![](../_assets/5_1_1.png)  
    - 입력 신호  
    제어기에 입력되는 신호를 설정합니다.  

    - 명령문  
    입력 신호가 OFF에서 ON될때 실행할 명령문을 기록합니다. 포지셔너 독립운전을 위해서는 move가 사용됩니다.  

    - 실행 중 출력신호  
    해당 명령문의 실행을 시작하면 ON되고, 실행이 완료되면 OFF됩니다.  

    - 실행완료 출력신호  
    해당 명령문의 실행을 시작하면 OFF되고, 실행이 완료되면 ON됩니다.  
    명령문 독립실행 관련한 자세한 내용은 [${cont_model} 제어기 조작설명서 - 7.5.10 명령문 독립 실행](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/ko-tp630/7-system/5-application-parameter/10-cmd-idp-exe?cont_model=${cont_model})를 참고하십시오.
  
2. 명령문 항목에 하기 버튼을 눌러 move문을 입력합니다.  
    부가축 move 명령을 독립적으로 수행시키기 위해서는 move문에 메커니즘을 지정해야 합니다.  
    move문 입력 관련한 자세한 내용은 [${cont_model} 제어기 기능설명서 - 로봇언어 HRScript - 5.1 포즈 (pose)](https://hrbook-hrc.web.app/#/view/doc-hrscript/ko/5-moving-robot/1-pose?cont_model=${cont_model})를 참고하십시오.

3. 부가축 move 독립 실행을 수행할 축을 axisctrl off 명령으로 설정합니다.  
    axisctrl 명령은 작업 프로그램에 의해 부가축의 제어를 할 것인지 여부를 선택하는 명령입니다. axisctrl off된 축은 작업 프로그램에 기록된 위치로 이동하지 않고 독립적으로 이동할 수 있습니다. axisctrl on된 축은 작업 프로그램에 기록된 위치로 이동합니다.  
    외부 입력 신호에 의한 move 독립 실행은 axisctrl off ~ axisctrl on 사이에 해당하는 부분에서만 유효합니다 axisctrl off인 상태에서, 명령문 독립실행에서 지정한 입력신호가 들어올 경우 move문을 수행합니다. axisctrl off인 축은 하기 그림 상단의 j_7과 같이 노란색 글씨로 표시됩니다.  
    ![](../_assets/5_1_2.png)  
    자세한 내용은 [${cont_model} 제어기 기능설명서 - 멀티태스킹 - 2.1.6 axisctrl](https://hrbook-hrc.web.app/#/view/doc-multi-task/ko/2-related-function/2-1-command-sentence/6-axisctrl?cont_model=${cont_model})을 참고하십시오.




{% hint style="warning" %}  

1. 명령문 독립실행에서 지정한 move의 메커니즘은 axisctrl off된 축으로만 구성되어 있어야만 합니다.   
2. axisctrl on 명령을 실행할 때 아직 독립실행이 완료되지 않은 경우에는 'E1455 (0축) 독립 
운전이 종료되지 않음' 에러가 발생하고 로봇 축은 정지합니다. 이때 독립 운전 축은 해당 위치까지 이동합니다.  
이는 독립 move 명령을 실행하는 시간보다 로봇의 작업프로그램의 실행 시간이 빠른 것이므로 프로그램을 조정하거나 axisctrl on 명령 위에 wait 명령을 이용하여 move 독립 실행 완료 신호가 출력된 경우를 검사하도록 변경하십시오.  

{% endhint %}

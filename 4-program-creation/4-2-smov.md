﻿# 4.2 smov


	 smov {스테이션 번호}, {보간방식}, {속도}, {Accuracy}, {Tool 번호}

1.	스테이션 번호 : 포지셔너 그룹 번호를 의미합니다. (S1~S4)
2.	보간 방식 : 작업물 상에서 직선(L) 혹은 원호(C) 보간을 할 수 있습니다.
3.	속도 : 작업물 위에서 로봇의 TCP가 이동하는 속도를 설정합니다.
4.	Accuracy : 작업물 위에서 직선, 원호 보간의 Accuracy를 설정합니다.
5.	Tool 번호 : 작업을 수행하는 로봇 툴 번호를 설정합니다.

smov 명령의 설정은 포지셔너 좌표계 위에서 결정되는 것입니다. 예를 들어 속도의 경우 포지셔너를 움직이면서 두 점을 직선으로 이동한 경우 포지셔너 위에서 TCP가 이동하는 속도가 설정됩니다.

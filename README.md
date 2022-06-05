# 20194068 이승찬 오픈소스 과제
### 목차
1) 리눅스 명령어 top
2) 리눅스 명령어 ps
3) 리눅스 명령어 jobs
4) 리눅스 명령어  kill
5) vim 에디터 매크로 사용법
---
## 1. 리눅스 명령어 top
top 명령어는 시스템의 프로세스와 메모리 사용 상태를 5초 간격으로 업데이트하여 화면에 출력한다. 

어떤 프로세스가 CPU를 많이 차지하고 있는지 체크할 때 실시간으로 보이기 때문에 유용하다.
+ 사용방법


|옵션|설명|
|:---:|--------|
|-b|배치모드로 정보를 출력합니다. 실시간 상화 대화형모드로 정보를 화면에 일렬로 출력합니다.|
|-d delay|지정한 시간(delay 초)의 간격으로 정보를 업데이트하여 출력합니다.|
|-i idle|토글값이 off일 때, idle 프로세스나 좀비 프로세스 정보를 출력하지 않습니다.|
|-n num|지정한 시간(num)만큼 업데이트 정보를 출력합니다.|
|-p pid|지정한 프로세스 ID(pid)의 정보만을 출력합니다.|
|-q|시간의 간격 없이 계속하여 업데이트 정보를 출력합니다.|
|-s|몇 개의 대화식 명령을 비활성화 합니다|
|-S|누적된 정보를 출력합니다.|

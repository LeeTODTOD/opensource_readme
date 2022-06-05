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
![11](https://user-images.githubusercontent.com/104582605/172049844-1277c567-0839-4fc2-8ed7-cd5f605b9cef.png)

맨 윗줄부터

16:25:10 현재 서버의 시간

1user : 한명의 사용자가 접속

load average : 부하율

tasks 에서 259 total은 257개의 프로세스가 가동중

2 running 2개의 프로세스가 실행중

257 sleeping : 257개의 프로세스가 대기중

0 stopped : 0개의 프로세스가 멈춤

0 zombie : 0개의 프로세스가 좀비상태

**-- CPU --**

%us  : 유저 레벨에서 사용하고 있는 CPU의 비중

%sy : 시스템 레벨에서 사용하고 있는 CPU비중

%id : 유휴 상태의 CPU 비중

%wa : 시스템이 I/O 요청을 처리하지 못한 상태에서의 CPU idle 상태인 비중

**-- 메모리 --**

Mem:   32946200total,  25504432k used,   7441768k free,  53460k buffers 

전체 물리적인 메모리, 사용중인 메모리(used), 사용되지 않는 여유 메모리(free), 버퍼된 메모리(buffers)

Swap:  17101184k total,    11708k used,  17089476k free,  22014132k cached 

전체 스왑 메모리, 사용중인 스왑 메모리, 남아있는 스왑메모리, 캐싱메모리

**-- 프로세스 상태 --**

PID : 프로세스 ID (PID)

USER : 프로세스를 실행시킨 사용자 ID

PRI : 프로세스의 우선순위 (priority)

NI : NICE 값. 일의 nice value값이다. 마이너스를 가지는 nice value는 우선순위가 높음.

VIRT : 가상 메모리의 사용량(SWAP+RES)

RES : 현재 페이지가 상주하고 있는 크기(Resident Size)

SHR : 분할된 페이지, 프로세스에 의해 사용된 메모리를 나눈 메모리의 총합.

S : 프로세스의 상태 [ S(sleeping), R(running), W(swapped out process), Z(zombies) ]

%CPU : 프로세스가 사용하는 CPU의 사용율

%MEM : 프로세스가 사용하는 메모리의 사용율

COMMAND : 실행된 명령어


+ 사용방법


```$ top 옵션```

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

+ top 실행후 명령어

|명령어|설명|
|:---:|--------|
|shift + p|CPU 사용률이 높은 프로세스 순서대로 표시|
|shift + m|메모리 사용률이 높은 프로세스 순서대로 표시|
|shift + t|프로세스가 돌아가고 있는 시간 순서대로 표시|
|- k|프로세스  kill  - k 입력 후 종료할 PID 입력 signal을 입력하라고 하면 kill signal인 9를 입력|
|- a|메모리 사용량에 따라 정렬|
|- h|도움말 |

## 2. 리눅스 명령어 ps
ps명령어는 현재 실행중인 프로세스 목록을 보여준다.

아파치,오라클 등 프로그램 프로세스가 정상적인지 확인하거나 비정상적인 프로세스가 올라왔는지 확인 하는 등 

리눅스 관리 전반적으로 많이 사용되는 명령어이다.

![22](https://user-images.githubusercontent.com/104582605/172051073-e71358c4-5f31-41b5-a8d7-5c76968c3ffa.png)

```$ ps 옵션```


|옵션|설명|
|:---:|--------|
|-A|모든 프로세스를 출력한다.|
|-a|세션 리더(일반적으로 로그인 셸)을 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력한다.|
|-e|커널 프로세스를 제외한 모든 프로세스를 출력해 준다.|
|-f|풀 포맷으로 보여준다  유닉스 스타일로 출력해주는 옵션으로 UID, PID, PPID등이 함께 표시된다.|
|-l (sys V) l (BSD계열) |긴 포맷으로 보여준다.  프로세스의 정보를 길게 보여주는 옵션으로 우선순위와 관련된 PRI와 NI값을 확인할 수 있다. |

**사용방법 예시**

```$ ps -ef```

모든 프로세스를 풀 포멧으로 출력

```$ ps -ef | grep '프로세스명'```

'프로세스명'의 프로세스 구동 

**출력 내용**
|행제목|내용|
|:---:|--------|
|UID|실행 유저|
|PID|프로세스 ID|
|PPID|부모 프로세스 PID|
|C|CPU 사용량|
|STIME|Strat Time|
|TTY|프로세스 제어 위치|
|TIME|구동 시간|
|CMD|실행 명령어|




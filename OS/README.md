# Part 1 운영체제
---
# 프로세스(Process)
---
## 프로세스가 무엇인가요?
- 답변 내용
  ### Q) Process와 Program 차이점 설명
  - 답변 내용
  ### Q) Process와 Thread 차이점 설명
  - 답변 내용
  
     ### Q-1) Light-weight process
     - 답변 내용
     ### Q-2) 멀티 프로세스, 멀티 스레드 정의와 속도 차이
     - 답변 내용
     ### Q-3) 크롬의 탭은 프로세스인가 스레드인가
     - 답변 내용
     
  ### Q) 프로세스와 스레드는 각각 어떻게 생성
  - 답변 내용
  ### Q) 프로세스 메모리 구조 설명
  - 답변 내용
      ### Q-1) 초기화 하지 않은 변수들
      - 답변 내용
      ### Q-2) 동적 라이브러리 접근
      - 답변 내용
      ### Q-3) Stack Size는 언제 결정되냐?
      - 답변 내용
      ### Q-4) 왜 Stack이 heap 보다 빠르냐?
      - 답변 내용
    
  ### Q) 프로세스 상태에는 어떤 것들이 있나요?
  - 답변 내용
      #### Q-1) non-preemptive 에서 있을 수가 없는 상태 변화
      - 답변 내용
    
      #### Q-2) Memory가 부족할 경우, Process는 어떠한 상태로 변하는가
      - 답변 내용
    
  ### Q) 좀비 프로세스, 고아 프로세스
  - 답변 내용

---
## 멀티 프로세스와 멀티 스레드에 대해 설명해주세요.

  ### Q) 멀티 프로세스와 멀티스레드
    - 멀티 프로세스
    하나의 응용프로그램을 여러개의 프로세스로 구성하여 각 프로세스마다 하나의 작업을 처리한다.
    장점
    - 독립된 구조로 안전성이 높은 장점이 있다.
    - 프로세스 중 하나에 문제가 생겨도 다른 프로세스에 영향을 주지 않아, 작업속도가 느려지는 손해정도는 생기지만 정지되거나 하는 문제는 발생하지 않는다.
    - 여러개의 프로세스가 처리되어야 할 때 동일한 데이터를 사용하고, 이러한 데이터를 하나의 디스크에 두고 모든 프로세서(CPU)가 이를 공유하면 비용적으로 저렴하다
    단점
    - 독립된 메모리 영역이기 때문에 작업량이 많을수록( Context Switching이 자주 일어나서 주소 공간의 공유가 잦을 경우) 오버헤드가 발생하여 성능저하가 발생 할 수 있다.
    - Context Switching 과정에서 캐시 메모리 초기화 등 무거운 작업이 진행되고 시간이 소모되는 등 오버헤드가 발생한다  
    
    - 멀티 스레드
    하나의 응용프로그램이 여러개의 스레드로 구성하고 각 스레드는 하나의 작업을 처리한다.
    장점
    - 시스템 처리속도가 빨라지고 자원의 낭비가 줄어들어 응답시간이 빨라진다
    단점
    -동기화를 통해 스레드의 작업 처리 순서와 공유 자원에 대한 접근을 컨트롤할 수 있다. 그러나 불필요한 부분까지 동기화를 하는 경우, 과도한 lock으로 인해 병목 현상을 발생시켜 성능이 저하될 가능성이 높기 때문에 주의해야 한다
  ### Q) 멀티 스레드랑 싱글 스레드 차이
    - 싱글스레드
    하나의 프로세스에서 오직 하나의 스레드로만 실행한다.
    장점
    - 문맥 교환(context switch) 작업을 요구하지 않는다.
    - 자원 접근에 대한 동기화를 신경쓰지 않아도 된다
    - 단순히 CPU만을 사용하는 계산작업이라면, 오히려 멀티스레드보다 싱글스레드로 프로그래밍-하는 것이 더 효율적이다.
    - 프로그래밍 난이도가 쉽고, CPU, 메모리를 적게 사용한다.
    단점
    - 여러 개의 CPU를 활용하지 못한다.
    -연산량이 많은 작업을 하는 경우, 그 작업이 완료되어야 다른 작업을 수행할 수 있다.
    -글 스레드 모델은 에러 처리를 못하는 경우 멈춘다.
  ### Q) 각각의 종류가 유리한 경우와 종류
    멀티프로세스 - 독립적인 구조로 안정성이 높기 때문에 안정성이 중요한 작업일 경우 유리하다.
    멀티스레드 - 복잡한 처리나 대용량 데이터, 다중서버를 다루는 작업일 경우 전체 소요 시간 및 성능 향상의 이점을 가져오기 위해 멀티스레드 방식을 선택
  ### Q) 오버헤드가 발생하는 이유
    특정 기능을 수행하기 위해 간접적으로 걸리는 시간과 메모리들의 값으로 작업량이 많은 작업일 경우 프로세스가 교체해 가면 작업 하기때문에 해당 한 프로세스의 작업 마무리 시간보다 더 걸리게 된다.
    해결방안
    - 프로그램 다중화 수준을 낮춘다(문맥교환 발생빈도 감소)
    - 스레드 이용(스레드를 이용하여 문맥교환 부하를 최소화한다)
    - 스택포인터 활용(스택 이용 프로그램의 경우 스택 포인터를 이용하여 문맥교환 부하 최소화)
  ### Q) 그럼 웹서버의 상태별로 스레드가 적합할 때와 프로세스가 적합할 때를 설명해주세요. 이유도 함께 설명해주세요.
    스레드: 하나의 응용프로그램을 여러개를 띄어 작업하는 것 보다 하나의 응용프로그램으로 여러 작업을 할 수 있을때 유리(파워포인터.. 등)  
    프로세스: 각 작업이 독립적이고 다른 프로세스에 영향을 주지 않아야 할 경우(계산기.. 등)


---
## PCB에 대해 설명해주세요.
- 답변 내용
  ### Q) 스레드는 PCB를 갖고 있을까요?
  - 답변 내용
  ### Q) 자식 프로세스가 상태를 알리지 않고 죽거나, 부모 프로세스가 먼저 죽게 되면 어떻게 처리하나요?
  - 답변 내용
  ### Q) 프로세스 주소공간에 대해 설명해 주세요.
  - 답변 내용
      ### Q-1) 초기화 하지 않은 변수들은 어디에 저장될까요?
      - 답변 내용  
      ### Q-2) 일반적인 주소공간 그림처럼, Stack과 Heap의 크기는 매우 크다고 할 수 있을까요? 그렇지 않다면, 그 크기는 언제 결정될까요?
      - 답변 내용
      ### Q-3) Stack과 Heap 공간에 대해, 접근 속도가 더 빠른 공간은 어디일까요?
      - 답변 내용
      ### Q-4) 다음과 같이 공간을 분할하는 이유가 있을까요?
      - 답변 내용
      ### Q-5) 스레드의 주소공간은 어떻게 구성되어 있을까요?
      - 답변 내용


---
## 컨텍스트 스위칭 시에는 어떤 일들이 일어나나요?
- 컨텍스트 스위칭은 CPU가 하나 이상의 프로세스를 처리할 때 발생합니다. 이때 현재 실행 중인 프로세스의 상태를 보관하고, 다음 실행할 프로세스의 상태를 불러오는 작업이 수행됩니다. 이는 CPU의 처리 시간을 분할하여 여러 프로세스가 동시에 실행될 수 있도록 하기 위해 필요합니다.

  ### Q) 컨텍스트 스위칭은 언제 일어날까요?
  - 프로세스와 스레드는 모두 실행 중인 프로그램의 단위입니다. 하지만 컨텍스트 스위칭(Context Switching)에 대한 처리 방식에서 차이가 있습니다.
  프로세스는 각각 독립된 메모리 공간을 가지고 있기 때문에, 프로세스 간 컨텍스트 스위칭이 발생하면, 현재 실행 중인 프로세스의 상태 정보를 PCB(Process Control Block)에 저장한 후, 새로운 프로세스의 PCB로 전환하여 해당 프로세스를 실행합니다. 이는 새로운 프로세스가 시작되는 것과 동일합니다.
스레드는 하나의 프로세스 내에서 실행되기 때문에, 컨텍스트 스위칭이 발생하면, 스레드 간의 스택, 레지스터 값 등의 상태 정보만 전환하면 됩니다. 따라서, 스레드 간의 컨텍스트 스위칭은 프로세스 간의 컨텍스트 스위칭보다 훨씬 빠릅니다.


  ### Q) 프로세스와 쓰레드는 컨텍스트 스위칭이 발생했을 때 어떤 차이가 있을까요?
  - 프로세스와 쓰레드는 모두 컨텍스트 스위칭이 발생했을 때 다음에 실행할 코드와 상태를 저장하고 복원하는 작업이 필요합니다. 하지만 그들 간에 컨텍스트 스위칭에는 몇 가지 차이점이 있습니다.

    프로세스는 운영 체제에서 독립적인 실행 단위입니다. 프로세스 간에는 각자의 독립적인 가상 메모리 공간이 할당되며, 이러한 가상 메모리 공간은 다른 프로세스에서 접근할 수 없습니다. 따라서 프로세스 간에는 데이터를 공유하기 위해 명시적인 IPC(Inter-Process Communication) 메커니즘이 필요합니다. 프로세스 간에 컨텍스트 스위칭이 발생하면, 현재 실행 중인 프로세스의 상태와 가상 메모리 정보가 저장되고, 다음 실행할 프로세스의 상태와 가상 메모리 정보가 복원됩니다.

    반면에 쓰레드는 하나의 프로세스 내에서 실행되는 실행 단위입니다. 쓰레드는 동일한 가상 메모리 공간을 공유하므로, 데이터 공유에 대한 별도의 IPC 메커니즘이 필요하지 않습니다. 쓰레드 간에 컨텍스트 스위칭이 발생하면, 현재 실행 중인 쓰레드의 상태가 저장되고, 다음 실행할 쓰레드의 상태가 복원됩니다.

    따라서, 프로세스와 쓰레드 간의 가장 큰 차이점은 가상 메모리 공간을 공유하는지 여부입니다. 프로세스는 독립적인 실행 단위이기 때문에, 프로세스 간에는 데이터 공유를 위해 별도의 IPC 메커니즘이 필요합니다. 쓰레드는 하나의 프로세스 내에서 실행되는 실행 단위이므로, 데이터 공유를 위한 IPC 메커니즘이 필요하지 않습니다.
 
  ### Q) 컨텍스트 스위칭이 발생할 때, 기존의 프로세스 정보는 커널스택에 어떠한 형식으로 저장되나요?
  - 컨텍스트 스위칭이 발생할 때, 기존의 프로세스 정보는 PCB(Process Control Block)라는 구조체에 저장됩니다. 이 구조체에는 프로세스의 상태, 레지스터 값, 실행 위치 등의 정보가 저장되며, PCB는 커널스택에 저장됩니다. 다음에 실행될 프로세스의 PCB가 커널스택에서 불러와지고, 해당 프로세스의 상태가 복원됩니다.

  
---
## 프로세스 스케줄링 알고리즘에는 어떤 것들이 있나요?
- 프로세스 스케줄링 알고리즘에는 다양한 알고리즘이 있지만, 일반적으로 다음과 같은 알고리즘이 사용됩니다.
  
		FCFS(First-Come, First-Served) : 먼저 도착한 프로세스가 먼저 실행되는 알고리즘입니다.
		SJF(Shortest Job First) : 실행 시간이 가장 짧은 작업을 우선적으로 처리하는 알고리즘입니다.
		Priority Scheduling : 우선순위가 높은 작업을 먼저 실행하는 알고리즘입니다.
		Round-Robin : 각 프로세스가 일정 시간 동안 CPU를 할당받고, 시간이 지나면 다른 프로세스에게 CPU를 넘겨주는 알고리즘입니다.
		Multilevel Queue : 프로세스를 여러 개의 큐로 나누어 각 큐마다 다른 스케줄링 알고리즘을 적용하는 알고리즘입니다.
		Multilevel Feedback Queue : Multilevel Queue 알고리즘과 비슷하지만, 각 큐에서 실행되는 프로세스의 우선순위를 동적으로 변경해줍니다.
    이 외에도 다양한 스케줄링 알고리즘이 있으며, 실제 운영체제에서는 이러한 알고리즘들을 조합하여 최적화된 스케줄링을 수행합니다.
  
  ### Q) Preemptive / Non-Preemptive
  - Preemptive(선점형) 스케줄링과 Non-preemptive(비선점형) 스케줄링은 프로세스 스케줄링에서 중요한 개념입니다.
    Preemptive 스케줄링은 운영체제가 CPU를 점유하고 있는 프로세스를 강제로 중지시키고 다른 프로세스에게 CPU를 할당할 수 있는 방식입니다. 이는 우선순위가 높은 프로세스나시간 할당량이 끝난 프로세스 등이 다른 프로세스에게 CPU를 빠르게 양도할 수 있게 해줍니다.
    Non-preemptive 스케줄링은 한 프로세스가 CPU를 점유하는동안 다른 프로세스는 대기해야 합니다. CPU를 점유하는 프로세스가 종료되거나 대기 상태로 들어가야만 다른 프로세스가 CPU를 사용할 수 있습니다.
    Preemptive 스케줄링은 Non-preemptive 스케줄링보다 우선순위나 프로세스 상태 변화 등을 더 빠르게 반영할 수 있으나, 컨텍	스트 스위칭이 자주 일어나게 되어 오버헤드가 발생할 수 있습니다. 반면 Non-preemptive 스케줄링은 컨텍스트 스위칭이 적게 발생하여 오버헤드가 적지만, 우선순위가 높은 프로세스가 대기할 때 다른 프로세스들이 CPU를 사용할 수 없으므로 성능 저하가 발생할 수 있습니다.
	
  ### Q) Multi-level feedback Queue가 왜 나왔는지?
  - 답변 내용
  ### Q) Linux의 Process Scheduling?
  - 답변 내용
  ### Q) RR을 사용할 때, Time Slice에 따른 trade-off를 설명해 주세요.
  - 답변 내용
  ### Q) 싱글 스레드 CPU 에서 상시로 돌아가야 하는 프로세스가 있다면, 어떤 스케쥴링 알고리즘을 사용하는 것이 좋을까요? 또 왜 그럴까요
  - 답변 내용
  ### Q) 동시성과 병렬성의 차이에 대해 설명해 주세요.
  - 답변 내용
  ### Q) 타 스케쥴러와 비교하여, Multi-level Feedback Queue는 어떤 문제점들을 해결한다고 볼 수 있을까요?
  - 답변 내용
---
## 단기, 중기, 장기 스케쥴러란?
  ### Q) 현대 OS에는 단기, 중기, 장기 스케쥴러를 모두 사용하고 있나요?
  - 답변 내용
  ### Q) 프로세스의 스케쥴링 상태에 대해 설명해 주세요.
  - 답변 내용
  ### Q) preemptive/non-preemptive 에서 존재할 수 없는 상태가 있을까요?
  - 답변 내용
  ### Q) Memory가 부족할 경우, Process는 어떠한 상태로 변화할까요?
  - 답변 내용	

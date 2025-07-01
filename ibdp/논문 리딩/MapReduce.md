2025.06.30 ~ 2025.07.01
# MapReduce: Simplified Data Processing on Large Clusters

### [1-1]  
**Original:**  
MapReduce is a programming model and an associated implementation for processing and generating large datasets that is amenable to a broad variety of real-world tasks.  

**Translation:**  
MapReduce는 다양한 실제 작업에 적합한 대규모 데이터셋을 처리하고 생성하기 위한 프로그래밍 모델이자 그에 따른 구현체이다.

---

### [1-2]  
**Original:**  
Users specify the computation in terms of a map and a reduce function, and the underlying runtime system automatically parallelizes the computation across large-scale clusters of machines, handles machine failures, and schedules inter-machine communication to make efficient use of the network and disks.  

**Translation:**  
사용자는 계산을 map 함수와 reduce 함수로 정의하고, 하위 런타임 시스템은 자동으로 대규모 클러스터 전반에 걸쳐 연산을 병렬화하며, 장애 처리와 네트워크 및 디스크의 효율적 사용을 위한 통신 스케줄링도 담당한다.

---

### [1-3]  
**Original:**  
Programmers find the system easy to use: more than ten thousand distinct MapReduce programs have been implemented internally at Google over the past four years, and an average of one hundred thousand MapReduce jobs are executed on Google’s clusters every day, processing a total of more than twenty petabytes of data per day.  

**Translation:**  
프로그래머들은 이 시스템이 사용하기 쉽다고 느낀다. 지난 4년 동안 Google 내부에서 1만 개 이상의 고유한 MapReduce 프로그램이 구현되었고, 매일 평균 10만 개 이상의 MapReduce 작업이 Google 클러스터에서 실행되어 하루에 20페타바이트 이상의 데이터를 처리한다.

---

### [1-4]  
**Original:**  
Prior to our development of MapReduce, the authors and many others at Google implemented hundreds of special-purpose computations that process large amounts of raw data, such as crawled documents, Web request logs, etc., to compute various kinds of derived data, such as inverted indices, various representations of the graph structure of Web documents, summaries of the number of pages crawled per host, and the set of most frequent queries in a given day.  

**Translation:**  
MapReduce를 개발하기 전에, 저자들과 Google의 여러 엔지니어들은 수집한 문서나 웹 요청 로그 등 대량의 원시 데이터를 처리해 역색인, 웹 문서의 그래프 구조 표현, 호스트별 수집된 페이지 수 요약, 일일 최다 검색어 집합 등 다양한 파생 데이터를 계산하는 수백 개의 특수 목적 연산을 구현했다.

---

### [1-5]  
**Original:**  
Most such computations are conceptually straightforward. However, the input data is usually large and the computations have to be distributed across hundreds or thousands of machines in order to finish in a reasonable amount of time. The issues of how to parallelize the computation, distribute the data, and handle failures conspire to obscure the original simple computation with large amounts of complex code to deal with these issues.

**Translation:**  
이러한 연산 대부분은 개념적으로는 단순하다. 하지만 입력 데이터의 크기가 매우 크기 때문에, 이 연산을 합리적인 시간 내에 끝내려면 수백 또는 수천 대의 머신에 분산시켜야 한다. 계산을 병렬화하는 방법, 데이터를 분산하는 방식, 장애를 처리하는 문제들이 얽히면서, 원래는 단순했던 계산이 이러한 문제들을 처리하기 위한 복잡한 코드로 가려지게 된다.

---
### [1-6]  
**Original:**  
As a reaction to this complexity, we designed a new abstraction that allows us to express the simple computations we were trying to perform but hides the messy details of parallelization, fault tolerance, data distribution and load balancing in a library.

**Translation:**  
이러한 복잡성에 대응하기 위해, 우리는 수행하려던 단순한 연산을 그대로 표현하면서도 병렬화, 장애 허용, 데이터 분산, 그리고 부하 분산과 같은 복잡한 세부 사항은 라이브러리 안에 숨길 수 있는 새로운 추상화를 설계했다.

---
### [1-7]  
**Original:**  
Our abstraction is inspired by the map and reduce primitives present in Lisp and many other functional languages. We realized that most of our computations involved applying a map operation to each logical record in our input in order to compute a set of intermediate key/value pairs, and then applying a reduce operation to all the values that shared the same key in order to combine the derived data appropriately.

**Translation:**  
우리가 설계한 추상화는 Lisp 및 여러 함수형 언어에 존재하는 map과 reduce라는 기본 연산에서 영감을 받았다. 우리는 대부분의 연산이 입력의 각 논리 레코드에 map 연산을 적용해 중간 키/값 쌍을 만들고, 그 후 동일한 키를 가진 값들에 reduce 연산을 적용해 도출된 데이터를 적절히 결합하는 방식임을 깨달았다.

---
### [1-8]  
**Original:**  
Our use of a functional abstraction with simple semantics enabled us to parallelize large computations easily, and to use re-execution as the primary mechanism for fault tolerance. 

**Translation:**  
우리는 의미가 단순한 함수형 추상화를 사용함으로써 대규모 연산을 손쉽게 병렬화하고, 재실행을 장애 허용의 주요 메커니즘으로 활용할 수 있었다. 

---
### [1-9]  

**Original:**  
The major contributions of this work are a simple and powerful interface that enables automatic parallelization and distribution of large-scale computations, combined with an implementation of this interface that achieves high performance on large clusters of commodity PCs. The programming model can also be used to parallelize computations across multiple cores of the same machine.  


**Translation:**  
이 논문의 주요 기여는 대규모 연산을 자동으로 병렬화하고 분산 처리할 수 있는 **단순하면서도 강력한 인터페이스**를 제안한 것과, 이 인터페이스를 실제로 구현하여 범용 PC 수천 대로 구성된 대형 클러스터에서도 **고성능을 달성한 구현체**를 함께 제시한 것이다. 이 프로그래밍 모델은 하나의 머신 내 여러 코어 간의 병렬 처리에도 활용될 수 있다.  


---
### [1-10]  
**Original:**  
Section 2 describes the basic programming model and gives several examples. In Section 3, we describe an implementation of the MapReduce interface tailored towards our cluster-based computing environment. Section 4 describes several refinements of the programming model that we have found useful. Section 5 has performance measurements of our implementation for a variety of tasks. In Section 6, we explore the use of MapReduce within Google including our experiences in using it as the basis for a rewrite of our production indexing system. Section 7 discusses related and future work.

**Translation:**  
2장에서는 기본 프로그래밍 모델과 예제를 소개하고, 3장에서는 우리 클러스터 환경에 맞춘 MapReduce 인터페이스의 구현을 설명한다. 4장에서는 우리가 유용하게 사용한 몇 가지 모델 확장 기능을 소개하고, 5장에서는 다양한 작업에서의 구현 성능을 측정한 결과를 제시한다. 6장에서는 Google 내에서 MapReduce를 실제로 어떻게 사용해왔는지, 그리고 이를 기반으로 검색 인덱싱 시스템을 재작성한 경험을 공유한다. 마지막 7장에서는 관련 연구와 향후 과제를 논의한다.

---
### [2-1]

**Original:**  
The computation takes a set of input key/value pairs, and produces a set of output key/value pairs. The user of the MapReduce library expresses the computation as two functions: map and reduce.

**Translation:**  
이 계산은 **입력 키/값 쌍 집합을 받아서**, **출력 키/값 쌍 집합을 생성**한다.  
MapReduce 라이브러리의 사용자는 이 계산을 두 개의 함수인 **map**과 **reduce**로 표현한다.


---
### [2-2]

**Original:**  
Map, written by the user, takes an input pair and produces a set of intermediate key/value pairs. The MapReduce library groups together all intermediate values associated with the same intermediate key I and passes them to the reduce function.

**Translation:**  
사용자가 작성하는 **map 함수**는 입력 쌍 하나를 받아, **중간 키/값 쌍 집합**을 생성한다.  
MapReduce 라이브러리는 **같은 중간 키 I에 대응하는 모든 중간 값들을 모아서**, 그것들을 **reduce 함수에 전달**한다.

---
### [2-3]

**Original:**  
The reduce function, also written by the user, accepts an intermediate key I and a set of values for that key. It merges these values together to form a possibly smaller set of values. Typically just zero or one output value is produced per reduce invocation.

**Translation:**  
마찬가지로 사용자가 작성하는 **reduce 함수**는 **중간 키 I**와 그 키에 대응하는 **값들의 집합**을 입력으로 받는다.  
그리고 이 값들을 **병합하여 더 작은 값 집합으로 만든다**.  
일반적으로 reduce 함수가 호출될 때마다 **출력 값은 0개 또는 1개**만 생성된다.

---
### [2-4]

**Original:**  
The intermediate values are supplied to the user’s reduce function via an iterator. This allows us to handle lists of values that are too large to fit in memory.

**Translation:**  
중간 값들은 **이터레이터(iterator)**를 통해 reduce 함수에 제공된다.  
이는 **메모리에 한 번에 다 들어가지 않을 만큼 큰 값 목록**도 다룰 수 있도록 해준다.

---
### [2.1 예제]

**Original:**  
Consider the problem of counting the number of occurrences of each word in a large collection of documents. The user would write code similar to the following pseudocode.

**Translation:**  
많은 문서들 속에서 각 단어가 몇 번 나오는지를 세는 문제를 생각해보자. 사용자는 아래와 같은 유사 코드(pseudocode)를 작성하게 된다.

---

```java
map(String key, String value):
// key: 문서 이름
// value: 문서 내용
for each word w in value:
    EmitIntermediate(w, “1”);

```

```java
reduce(String key, Iterator values):
// key: 하나의 단어
// values: 해당 단어에 대한 숫자 리스트
int result = 0;
for each v in values:
    result += ParseInt(v);
Emit(AsString(result));

```

---
**Original:**  
The map function emits each word plus an associated count of occurrences (just 1 in this simple example). The reduce function sums together all counts emitted for a particular word.

**Translation:**  
`map` 함수는 각 단어에 대해 해당 단어와 그 등장 횟수(이 예제에서는 단순히 1)를 출력한다. `reduce` 함수는 특정 단어에 대해 `map` 함수가 출력한 모든 1을 더해서 최종 등장 횟수를 계산한다.

---
**Original:**  
In addition, the user writes code to fill in a mapreduce specification object with the names of the input and output files and optional tuning parameters. The user then invokes the MapReduce function, passing it to the specification object. The user’s code is linked together with the MapReduce library (implemented in C++).

**Translation:**  
추가로, 사용자는 입력 파일과 출력 파일의 이름, 그리고 선택적인 튜닝 파라미터들을 담은 **MapReduce 사양 객체(specification object)**를 작성한다. 이후 MapReduce 함수에 이 객체를 전달하여 호출하며, 이 사용자의 코드는 C++로 구현된 MapReduce 라이브러리와 함께 연결되어 실행된다.

---
**Original:**  
Our original MapReduce paper contains the full program text for this example [8].  
More than ten thousand distinct programs have been implemented using MapReduce at Google, including algorithms for large-scale graph processing, text processing, data mining, machine learning, statistical machine translation, and many other areas.

**Translation:**  
원래의 MapReduce 논문 [8]에는 이 예제에 대한 전체 코드가 수록되어 있다.  
Google 내부에서는 1만 개가 넘는 서로 다른 프로그램이 MapReduce를 사용해 구현되었으며, 그 예로는 대규모 그래프 처리, 텍스트 처리, 데이터 마이닝, 머신러닝, 통계적 기계 번역 등의 알고리즘이 있다.

---

**Original:**  
More discussion of specific applications of MapReduce can be found elsewhere [8, 16, 7].

**Translation:**  
MapReduce의 구체적인 응용 사례에 대한 더 자세한 논의는 다른 문헌들 [8, 16, 7]에서 확인할 수 있다.

---

### [2.2 타입]

**Original:**  
Even though the previous pseudocode is written in terms of string inputs and outputs, conceptually the map and reduce functions supplied by the user have associated types.  
map (k1,v1) → list(k2,v2)  
reduce (k2,list(v2)) → list(v2)

**Translation:**  
앞서 제시된 유사 코드는 문자열 입력과 출력만을 사용했지만, 개념적으로 보면 사용자 정의 map과 reduce 함수는 다음과 같은 **명시적인 타입**을 갖는다.

- `map (k1, v1) → list(k2, v2)`
    
- `reduce (k2, list(v2)) → list(v2)`
    

---

**Original:**  
That is, the input keys and values are drawn from a different domain than the output keys and values. Furthermore, the intermediate keys and values are from the same domain as the output keys and values.

**Translation:**  
즉, **입력 키와 값은 출력 키와 값과는 다른 타입일 수 있다**.  
또한 **중간 키와 값은 최종 출력 키와 값과 같은 도메인(형태, 타입)을 가진다**.

---
### [3. Implementation]

**원문:**  
Many different implementations of the MapReduce interface are possible.  
The right choice depends on the environment.  
For example, one implementation may be suitable for a small shared-memory machine, another for a large NUMA multiprocessor, and yet another for an even larger collection of networked machines.

**번역:**  
MapReduce 인터페이스에는 다양한 구현 방식이 가능하다.  
적절한 구현 방식은 사용 환경에 따라 달라진다.  
예를 들어, 어떤 구현은 **메모리를 공유하는 소형 머신**에 적합하고, 또 다른 구현은 **대형 NUMA(Non-Uniform Memory Access) 멀티프로세서** 환경에, 또 다른 구현은 **수천 대의 네트워크 연결된 머신 집합(클러스터)**에 적합할 수 있다.

---

**원문:**  
Since our original article, several open source implementations of MapReduce have been developed [1, 2], and the applicability of MapReduce to a variety of problem domains has been studied [7, 16].

**번역:**  
초기 논문 발표 이후, 여러 개의 **오픈소스 MapReduce 구현체**들이 개발되었고 [1, 2],  
MapReduce가 **다양한 문제 영역에 적용 가능한지에 대한 연구**도 진행되었다 [7, 16].

---

**원문:**  
This section describes our implementation of MapReduce that is targeted to the computing environment in wide use at Google:  
large clusters of commodity PCs connected together with switched Gigabit Ethernet [4].

**번역:**  
이번 섹션에서는 **Google에서 실제로 사용 중인 환경**을 기준으로 만든 MapReduce 구현에 대해 설명한다.  
이 환경은 범용 PC들로 구성된 대규모 클러스터이며, **스위칭 기가비트 이더넷(Gigabit Ethernet)**으로 연결되어 있다 [4].

---

**원문:**  
In our environment, machines are typically dual-processor x86 processors running Linux, with 4-8GB of memory per machine.  
Individual machines typically have 1 gigabit/second of network bandwidth, but the overall bisection bandwidth available per machine is considerably less than 1 gigabit/second.

**번역:**  
우리 환경의 각 머신은 일반적으로 **듀얼 프로세서 x86 CPU**에 리눅스를 운영체제로 사용하며, 메모리는 **4~8GB 수준**이다.  
개별 머신은 **1Gbps의 네트워크 대역폭**을 가지고 있지만, 전체 클러스터 내에서 머신 간 통신 시 실질적으로 사용할 수 있는 **중간 절단 대역폭(bisection bandwidth)**은 이보다 상당히 낮다.

---

**원문:**  
A computing cluster contains many thousands of machines, and therefore machine failures are common.

**번역:**  
이러한 컴퓨팅 클러스터는 수천 대의 머신으로 구성되기 때문에, 머신 고장은 **일상적으로 발생하는 상황**이다.

---

**원문:**  
Storage is provided by inexpensive IDE disks attached directly to individual machines.  
GFS, a distributed file system developed in-house [10], is used to manage the data stored on these disks.  
The file system uses replication to provide availability and reliability on top of unreliable hardware.

**번역:**  
스토리지는 각 머신에 직접 연결된 **저렴한 IDE 디스크**들로 구성된다.  
이 디스크에 저장된 데이터는 Google이 자체 개발한 **GFS(Google File System)** [10]이 관리한다.  
GFS는 하드웨어의 신뢰성이 낮기 때문에, **데이터를 복제(replication)**함으로써 **가용성과 안정성**을 보장한다.

---

**원문:**  
Users submit jobs to a scheduling system.  
Each job consists of a set of tasks, and is mapped by the scheduler to a set of available machines within a cluster.

**번역:**  
사용자는 작업(job)을 **스케줄링 시스템**에 제출한다.  
하나의 작업은 여러 개의 **작업 단위(task)**로 구성되며,  
스케줄러는 이를 클러스터 내에서 사용 가능한 머신들에 **자동으로 할당**한다.

---

---

### [3.1 Execution Overview]

**원문:**  
The map invocations are distributed across multiple machines by automatically partitioning the input data into a set of M splits.  
The input splits can be processed in parallel by different machines.

**번역:**  
Map 작업은 입력 데이터를 자동으로 **M개의 조각(split)**으로 분할하여  
**여러 대의 머신에 병렬로 분산 실행**함으로써 수행된다.

---

**원문:**  
Reduce invocations are distributed by partitioning the intermediate key space into R pieces using a partitioning function (e.g., `hash(key) mod R`).  
The number of partitions (R) and the partitioning function are specified by the user.

**번역:**  
Reduce 작업은 **중간 키 공간(intermediate key space)**을 **R개의 조각으로 분할**함으로써 배분되며,  
분할에는 보통 `hash(key) mod R` 같은 **파티셔닝 함수**가 사용된다.  
이 R 값과 함수는 사용자가 설정할 수 있다.

---

**원문:**  
Figure 1 shows the overall flow of a MapReduce operation in our implementation.  
When the user program calls the MapReduce function, the following sequence of actions occurs:

**번역:**  
Figure 1은 우리 구현에서의 **MapReduce 전체 동작 흐름**을 보여준다.  
사용자의 프로그램이 MapReduce 함수를 호출하면, **다음과 같은 순서로 동작**이 진행된다.

---
**원문:**  

1. The MapReduce library in the user program first splits the input files into M pieces of typically 16–64MB per piece (controllable by the user via an optional parameter). It then starts up many copies of the program on a cluster of machines.
    

**번역:**  

1. 사용자 프로그램 내의 MapReduce 라이브러리는 먼저 입력 파일을 M개의 조각으로 나눈다. 각 조각의 크기는 일반적으로 16~64MB이며, 이는 사용자가 선택적으로 조정할 수 있다. 그런 다음 클러스터 내 여러 머신에서 프로그램의 복사본들을 다수 실행시킨다.
    

---

**원문:**  
2. One of the copies of the program—the master—is special. The rest are workers that are assigned work by the master. There are M map tasks and R reduce tasks to assign. The master picks idle workers and assigns each one a map task or a reduce task.

**번역:**  
2. 실행된 프로그램 복사본 중 하나는 특별한 역할인 **마스터**로 지정된다. 나머지는 **워커**로서 마스터에 의해 작업을 할당받는다. 수행해야 할 작업은 M개의 map 작업과 R개의 reduce 작업으로 구성되며, 마스터는 유휴 상태인 워커를 선택해 각 워커에게 map 또는 reduce 작업을 할당한다.

---

**원문:**  
3. A worker who is assigned a map task reads the contents of the corresponding input split. It parses key/value pairs out of the input data and passes each pair to the user-defined map function. The intermediate key/value pairs produced by the map function are buffered in memory.

**번역:**  
3. map 작업을 할당받은 워커는 해당 입력 조각의 내용을 읽는다.  
그 후 입력 데이터를 key/value 쌍으로 파싱하고, 각 쌍을 사용자 정의 map 함수에 전달한다.  
map 함수가 생성한 중간 key/value 쌍들은 메모리에서 버퍼링된다.

---

**원문:**  
4. Periodically, the buffered pairs are written to local disk, partitioned into R regions by the partitioning function. The locations of these buffered pairs on the local disk are passed back to the master who is responsible for forwarding these locations to the reduce workers.

**번역:**  
4. 일정 주기마다, 버퍼에 저장된 중간 key/value 쌍은 로컬 디스크에 기록된다.  
이때 파티셔닝 함수에 의해 R개의 영역으로 나뉘어 저장되며,  
해당 쌍들의 디스크 내 위치 정보는 마스터에게 전달된다.  
마스터는 이 위치 정보를 reduce 워커에게 전달하는 역할을 맡는다.

---
**원문:**  
**5.** When a reduce worker is notified by the master about these locations,  
it uses remote procedure calls to read the buffered data from the local disks of the map workers.  
When a reduce worker has read all intermediate data for its partition,  
it sorts it by the intermediate keys so that all occurrences of the same key are grouped together.  
The sorting is needed because typically many different keys map to the same reduce task.  
If the amount of intermediate data is too large to fit in memory, an external sort is used.

**번역:**  
**5.** reduce 워커는 마스터로부터 이러한 위치 정보를 통보받으면,  
map 워커의 로컬 디스크에서 버퍼링된 데이터를 원격 프로시저 호출(Remote Procedure Call, RPC)을 통해 읽어온다.  
reduce 워커가 해당 파티션의 모든 중간 데이터를 읽으면,  
중간 key 기준으로 정렬하여 동일한 key의 모든 항목이 함께 묶이도록 한다.  
이러한 정렬은 보통 서로 다른 많은 key들이 동일한 reduce 작업에 매핑되기 때문에 필요하다.  
만약 중간 데이터가 메모리에 모두 담기에는 너무 크다면, 외부 정렬(external sort)이 사용된다.

---
**원문:**  
**6.** The reduce worker iterates over the sorted intermediate data  
and for each unique intermediate key encountered,  
it passes the key and the corresponding set of intermediate values to the user’s reduce function.  
The output of the reduce function is appended to a final output file for this reduce partition.

**번역:**  
**6.** reduce 워커는 정렬된 중간 데이터를 순회하며,  
발견되는 각 고유한 중간 key마다  
해당 key와 이에 대응되는 중간 값들의 집합을 사용자 정의 reduce 함수에 전달한다.  
reduce 함수의 출력은 이 reduce 파티션에 해당하는 최종 출력 파일에 추가된다.

---
**원문:**  
**7.** When all map tasks and reduce tasks have been completed,  
the master wakes up the user program.  
At this point, the MapReduce call in the user program returns back to the user code.  

---

**번역:**  
**7.** 모든 map 작업과 reduce 작업이 완료되면,  
마스터는 사용자 프로그램을 깨운다.  
이 시점에서, 사용자 프로그램 내에서 호출된 MapReduce 함수는 사용자 코드로 반환된다.  

---
**원문:**  
After successful completion, the output of the mapreduce execution is available in the R output files  
(one per reduce task, with file names specified by the user).  
Typically, users do not need to combine these R output files into one file;  
they often pass these files as input to another MapReduce call  
or use them from another distributed application that is able to deal with input that is partitioned into multiple files.

---

**번역:**  
성공적으로 완료된 후에는, MapReduce 실행 결과가 R개의 출력 파일에 저장되어 사용 가능하다  
(각 reduce 작업마다 하나의 파일이 생성되며, 파일 이름은 사용자가 지정함).  
일반적으로 사용자들은 이 R개의 출력 파일을 하나로 병합할 필요가 없으며,  
이 파일들을 **다음 MapReduce 호출의 입력으로 넘기거나**,  
**여러 파일로 분할된 입력을 처리할 수 있는 다른 분산 애플리케이션에서 바로 사용**하는 경우가 많다.

---
**원문:**  
**3.2 Master Data Structures**  
The master keeps several data structures. For each map task and reduce task, it stores the state (idle, in-progress, or completed) and the identity of the worker machine (for nonidle tasks).  
The master is the conduit through which the location of intermediate file regions is propagated from map tasks to reduce tasks.  
Therefore, for each completed map task, the master stores the locations and sizes of the R intermediate file regions produced by the map task.  
Updates to this location and size information are received as map tasks are completed.  
The information is pushed incrementally to workers that have in-progress reduce tasks.

**번역:**  
**3.2 마스터 데이터 구조**  
마스터는 여러 종류의 데이터 구조를 유지한다. 각 map 작업과 reduce 작업에 대해, 마스터는 해당 작업의 상태(대기 중, 실행 중, 완료됨)와 작업이 실행 중인 경우 그 작업을 수행 중인 워커 머신의 정보를 저장한다.  
또한 마스터는 map 작업에서 생성된 중간 파일 위치 정보를 reduce 작업에 전달하는 **정보 전달자(conduit)** 역할을 수행한다.  
따라서 마스터는 완료된 각 map 작업마다, 해당 작업이 생성한 **R개의 중간 파일 조각의 위치와 크기**를 기록한다.  
이러한 위치 및 크기 정보는 map 작업이 완료되면서 마스터에 전달되며,  
마스터는 이 정보를 reduce 작업을 수행 중인 워커들에게 **점진적으로 전달(push)** 한다.

---
**원문:**  
**3.3 Fault Tolerance**  
Since the MapReduce library is designed to help process very large amounts of data using hundreds or thousands of machines, the library must tolerate machine failures gracefully.

**번역:**  
**3.3 장애 허용성**  
MapReduce 라이브러리는 수백~수천 대의 머신을 이용해 대규모 데이터를 처리할 수 있도록 설계되었기 때문에,  
이러한 환경에서 발생할 수 있는 **머신의 고장을 시스템이 자연스럽고 문제없이 감내할 수 있도록** 만들어져야 한다.

---
**원문:**  
**Handling Worker Failures**  
The master pings every worker periodically. If no response is received from a worker in a certain amount of time, the master marks the worker as failed. Any map tasks completed by the worker are reset back to their initial idle state and therefore become eligible for scheduling on other workers. Similarly, any map task or reduce task in progress on a failed worker is also reset to idle and becomes eligible for rescheduling.  

---

**번역:**  
**작업자 장애 처리**  
마스터는 모든 작업자(worker)에게 주기적으로 핑(ping)을 보냅니다. 특정 시간 안에 응답이 없으면, 해당 작업자는 **장애 상태로 간주**됩니다.  
해당 작업자가 수행을 마친 **map 작업은 초기 상태로 되돌아가며**, 다른 작업자에게 재할당될 수 있도록 준비됩니다. 마찬가지로, **해당 작업자가 진행 중이던 map 또는 reduce 작업도 idle 상태로 전환되어 다시 스케줄링 대상이 됩니다.**

---
**원문:**  
Completed map tasks are reexecuted on a failure because their output is stored on the local disk(s) of the failed machine and is therefore inaccessible. Completed reduce tasks do not need to be reexecuted since their output is stored in a global file system.  

---

**번역:**  
완료된 **map 작업의 결과는 해당 작업자의 로컬 디스크에 저장**되므로, 장애가 발생하면 접근할 수 없게 됩니다. 따라서 **이러한 map 작업은 반드시 다시 실행됩니다.**  
반면에, 완료된 **reduce 작업의 결과는 글로벌 파일 시스템에 저장**되므로, **재실행이 필요 없습니다.**

---
**원문:**  
When a map task is executed first by worker A and then later executed by worker B (because A failed), all workers executing reduce tasks are notified of the reexecution. Any reduce task that has not already read the data from worker A will read the data from worker B.  

---

**번역:**  
예를 들어, **어떤 map 작업이 처음엔 작업자 A에서 실행되었지만**, A가 실패하여 나중에 **작업자 B에서 다시 실행되었다면**, **reduce 작업을 수행 중인 모든 작업자는 그 사실을 통보**받습니다.  
그리고 **아직 작업자 A의 데이터를 읽지 않은 reduce 작업자는 작업자 B의 데이터를 읽게 됩니다.**

---
**원문:**  
MapReduce is resilient to large-scale worker failures. For example, during one MapReduce operation, network maintenance on a running cluster was causing groups of 80 machines at a time to become unreachable for several minutes. The MapReduce master simply reexecuted the work done by the unreachable worker machines and continued to make forward progress, eventually completing the MapReduce operation.

---

**번역:**  
MapReduce는 **대규모 작업자 장애에도 견고**합니다. 실제로 한 번은 네트워크 유지보수로 인해 클러스터의 **80대에 달하는 머신이 수 분간 접근 불가능**해졌습니다.  
이때도 MapReduce 마스터는 단순히 해당 작업들의 **재실행만으로 문제를 해결**했고, 작업은 중단 없이 계속 진행되어 최종적으로 성공적으로 완료되었습니다.

---
**원문:**  
**Semantics in the Presence of Failures**  
When the user-supplied map and reduce operators are deterministic functions of their input values, our distributed implementation produces the same output as would have been produced by a nonfaulting sequential execution of the entire program.

---

**번역:**  
**장애 상황에서의 의미론(Semantics in the Presence of Failures)**  
사용자가 작성한 map 및 reduce 연산자가 **입력값에 대해 결정적(deterministic)**인 함수라면,  
MapReduce의 분산 실행 결과는 **오류 없이 순차적으로 실행했을 때와 동일한 출력**을 보장한다.

---
**원문:**  
We rely on atomic commits of map and reduce task outputs to achieve this property. Each in-progress task writes its output to private temporary files. A reduce task produces one such file, and a map task produces R such files (one per reduce task). 

---

**번역:**  
이러한 특성을 보장하기 위해, MapReduce는 **map 및 reduce 작업 결과의 원자적 커밋(atomic commit)**을 활용한다.  
실행 중인 각 작업은 결과를 **개별 임시 파일(private temporary files)**에 기록한다.  
reduce 작업은 하나의 임시 파일을 생성하고, map 작업은 **reduce 작업 수(R)**만큼의 임시 파일을 생성한다.

---
**원문:**  
When a map task completes, the worker sends a message to the master and includes the names of the R temporary files in the message. If the master receives a completion message for an already completed map task, it ignores the message. Otherwise, it records the names of R files in a master data structure.


---

**번역:**  
map 작업이 완료되면, 해당 작업자는 마스터에게 **임시 파일들의 이름을 포함한 완료 메시지**를 전송한다.  
만약 마스터가 이미 완료된 map 작업의 메시지를 다시 받으면 **이를 무시**하고,  
아닌 경우에는 **임시 파일들의 경로를 마스터의 데이터 구조에 저장**한다.


---
**원문:**  

When a reduce task completes, the reduce worker atomically renames its temporary output file to the final output file. If the same reduce task is executed on multiple machines, multiple rename calls will be executed for the same final output file. We rely on the atomic rename operation provided by the underlying file system to guarantee that the final file system state contains only the data produced by one execution of the reduce task.

---

**번역:**  
reduce 작업이 완료되면, reduce 작업자는 **임시 파일을 최종 출력 파일로 원자적으로 rename**한다.  
동일한 reduce 작업이 여러 머신에서 동시에 수행된 경우에도,  
**파일 시스템의 rename 연산이 원자적이기 때문에** 결국 하나의 실행 결과만이 최종 파일로 남는다.

---
**원문:**  

The vast majority of our map and reduce operators are deterministic, and the fact that our semantics are equivalent to a sequential execution in this case makes it very easy for programmers to reason about their program’s behavior. 

---

**번역:**  

대부분의 map 및 reduce 함수는 **결정적**이기 때문에,  
**개발자는 프로그램의 동작 결과를 순차 실행처럼 직관적으로 예측**할 수 있다.

---
**원문:**  

 When the map and/or reduce operators are nondeterministic, we provide weaker but still reasonable semantics. In the presence of nondeterministic operators, the output of a particular reduce task R1 is equivalent to the output for R1 produced by a sequential execution of the nondeterministic program. However, the output for a different reduce task R2 may correspond to the output for R2 produced by a different sequential execution of the nondeterministic program.

---

**번역:**  

그러나 map 또는 reduce 함수가 **비결정적(nondeterministic)**이라면,  
결과는 다소 달라질 수 있지만, 여전히 **타당한 수준의 의미론적 일관성**은 유지된다.  
이 경우 특정 reduce 작업 R1의 출력은 **순차 실행 시의 R1 결과와 동일**하지만,  
다른 reduce 작업 R2는 **다른 실행에서 생성된 map 출력에 기반한 결과**를 가질 수도 있다.

---
**원문:**  

Consider map task M and reduce tasks R1 and R2. Let e(Ri) be the execution of R1 that committed (there is exactly one such execution). The weaker semantics arise because e(R1) may have read the output produced by one execution of M, and e(R2) may have read the output produced by a different execution of M.

---

**번역:**  

예를 들어, map 작업 M과 reduce 작업 R1, R2가 있다고 하자.  
`e(Ri)`는 R1의 최종 커밋된 실행이라 할 때,  
`e(R1)`은 map 작업 M의 한 실행 결과를 읽었고,  
`e(R2)`는 M의 **다른 실행 결과**를 읽었을 수 있으므로,  
**완전한 일관성은 없지만 합리적인 수준의 결과를 보장한다.**

---
**원문:**  
Network bandwidth is a relatively scarce resource in our computing environment.  
We conserve network bandwidth by taking advantage of the fact that the input data (managed by GFS [10]) is stored on the local disks of the machines that make up our cluster.

---

**번역:**  
우리의 컴퓨팅 환경에서는 **네트워크 대역폭이 상대적으로 제한적인 자원**이다.  
MapReduce는 **입력 데이터(GFS가 관리함)**가 클러스터를 구성하는 **각 머신의 로컬 디스크에 저장되어 있다는 점을 활용하여**, 네트워크 대역폭 사용을 절약한다.

---

**원문:**  
GFS divides each file into 64MB blocks and stores several copies of each block (typically 3 copies) on different machines.  
The MapReduce master takes the location information of the input files into account and attempts to schedule a map task on a machine that contains a replica of the corresponding input data.

---

**번역:**  
GFS는 각 파일을 **64MB 블록 단위로 분할하고**, 각 블록을 **서로 다른 머신에 보통 3개의 복제본**으로 저장한다.  
MapReduce의 마스터는 **입력 파일의 위치 정보를 고려하여**, 해당 입력 데이터를 포함하고 있는 **복제본 머신에 map 작업을 우선 할당**하려 한다.

---

**원문:**  
Failing that, it attempts to schedule a map task near a replica of that task’s input data (e.g., on a worker machine that is on the same network switch as the machine containing the data).

---

**번역:**  
해당 머신에서 실행할 수 없는 경우에는, **그 데이터 복제본과 가까운 위치의 작업자 머신**에 map 작업을 할당하려 시도한다.  
예를 들어, **데이터를 가진 머신과 동일한 네트워크 스위치에 연결된 작업자 머신**이 이에 해당한다.

---

**원문:**  
When running large MapReduce operations on a significant fraction of the workers in a cluster, most input data is read locally and consumes no network bandwidth.

---

**번역:**  
클러스터 내 많은 작업자들이 참여하는 **대규모 MapReduce 작업**이 실행될 때,  
대부분의 입력 데이터는 **로컬 디스크에서 직접 읽히므로 네트워크 대역폭을 전혀 사용하지 않는다.**

---

**원문:**  
We subdivide the map phase into M pieces and the reduce phase into  
R pieces as described previously. Ideally, M and R should be much  
larger than the number of worker machines. Having each worker perform  
many different tasks improves dynamic load balancing and also  
speeds up recovery when a worker fails: the many map tasks it has  
completed can be spread out across all the other worker machines.

---

**번역:**  
우리는 map 단계는 **M개의 조각**, reduce 단계는 **R개의 조각**으로 나누어 처리합니다(앞서 설명한 대로).  
**이론적으로는 M과 R이 worker 머신 수보다 훨씬 많은 것이 이상적**입니다.  
이렇게 하면 각 worker가 다양한 작업을 수행하게 되어 **동적 부하 분산(load balancing)**이 개선되고,  
**작업자 장애 발생 시에도 빠른 복구가 가능합니다.**  
즉, 실패한 worker가 수행하던 다수의 map 작업들을 **다른 머신에 고르게 분산시킬 수 있기 때문입니다.**

---

**원문:**  
There are practical bounds on how large M and R can be in our implementation  
since the master must make O(M+R) scheduling decisions  
and keep O(M×R) state in memory as described. (The constant factors  
for memory usage are small, however. The O(M×R) piece of the state  
consists of approximately one byte of data per map task/ reduce task pair.)

---

**번역:**  
하지만 현실적으로는 M과 R을 너무 크게 잡을 수는 없습니다.  
왜냐하면 **마스터가 M + R개의 작업을 스케줄링해야 하고**,  
또한 **M × R 크기의 상태 정보를 메모리에 유지**해야 하기 때문입니다.  
(다만, 메모리 사용량의 상수 계수는 작습니다.  
M × R 크기의 상태 정보는 map 작업과 reduce 작업 쌍마다 약 1바이트 정도의 정보만 필요합니다.)

---

**원문:**  
Furthermore, R is often constrained by users because the output of  
each reduce task ends up in a separate output file. In practice, we tend  
to choose M so that each individual task is roughly 16MB to 64MB of  
input data (so that the locality optimization described previously is most  
effective), and we make R a small multiple of the number of worker  
machines we expect to use. We often perform MapReduce computations  
with M = 200,000 and R = 5,000, using 2,000 worker machines.

---

**번역:**  
또한, R 값은 사용자에 의해 제한되는 경우가 많습니다.  
왜냐하면 **각 reduce 작업의 출력은 별도의 출력 파일로 저장되기 때문입니다.**  
실제로 우리는 각 map 작업이 **16MB에서 64MB 정도의 입력 데이터**를 처리하도록 M을 설정합니다.  
이렇게 하면 앞서 설명한 **데이터 지역성(locality)** 최적화 효과를 최대화할 수 있습니다.  
그리고 R 값은 일반적으로 예상하는 worker 머신 수의 **작은 배수**로 설정합니다.  
실제로 우리는 종종 **worker 2,000대에 M = 200,000, R = 5,000**으로 MapReduce 작업을 수행합니다.

---
**원문:**  
One of the common causes that lengthens the total time taken for a MapReduce operation is a straggler,  
that is, a machine that takes an unusually long time to complete one of the last few map or reduce tasks in the computation.

**번역:**  
MapReduce 작업에서 **전체 처리 시간을 불필요하게 길게 만드는 대표적인 원인 중 하나는 '스트래글러(straggler)'**입니다.  
이는 전체 작업 중 **마지막 몇 개 map 또는 reduce 작업이 특정 머신에서 비정상적으로 오래 걸리는 현상**을 말합니다.

---

**원문:**  
Stragglers can arise for a whole host of reasons.  
For example, a machine with a bad disk may experience frequent correctable errors  
that slow its read performance from 30MB/s to 1MB/s.

**번역:**  
스트래글러는 **여러 가지 다양한 원인**으로 발생할 수 있습니다.  
예를 들어, **디스크 상태가 좋지 않은 머신**은 자주 발생하는 오류 수정 작업 때문에  
**읽기 속도가 30MB/s에서 1MB/s로 급격히 느려질 수 있습니다.**

---

**원문:**  
The cluster scheduling system may have scheduled other tasks on the machine,  
causing it to execute the MapReduce code more slowly  
due to competition for CPU, memory, local disk, or network bandwidth.

**번역:**  
또는 클러스터 스케줄러가 해당 머신에 **다른 작업을 함께 배정**했을 수도 있습니다.  
이로 인해 CPU, 메모리, 디스크, 네트워크 대역폭 등을 두고 **자원 경합이 발생**하고,  
그 결과 MapReduce 작업의 **처리 속도가 느려질 수 있습니다.**

---

**원문:**  
A recent problem we experienced was a bug in machine initialization code  
that caused processor caches to be disabled:  
computations on affected machines slowed down by over a factor of one hundred.

**번역:**  
실제로 우리가 겪었던 문제 중 하나는, **머신 초기화 코드에 버그가 있어서 CPU 캐시가 비활성화**된 경우였습니다.  
이로 인해 해당 머신들의 연산 속도는 **무려 100배 이상 느려졌습니다.**

---

**원문:**  
We have a general mechanism to alleviate the problem of stragglers.

**번역:**  
이러한 스트래글러 문제를 해결하기 위해 우리는 **일반적인 해결 메커니즘**을 마련했습니다.

---

**원문:**  
When a MapReduce operation is close to completion,  
the master schedules backup executions of the remaining in-progress tasks.

**번역:**  
MapReduce 작업이 거의 완료될 시점이 되면,  
**마스터는 아직 끝나지 않은 작업들에 대해 '백업 실행(backup execution)'을 추가로 시작**합니다.

---

**원문:**  
The task is marked as completed whenever either the primary or the backup execution completes.

**번역:**  
이때 **기존 작업(primary)**이든 **백업 작업**이든  
**둘 중 하나만 완료되면 해당 작업은 전체적으로 '완료됨'으로 처리**됩니다.

---

**원문:**  
We have tuned this mechanism so that it typically increases  
the computational resources used by the operation by no more than a few percent.

**번역:**  
이 메커니즘은 전체 작업에서 사용하는 **컴퓨팅 자원을 몇 퍼센트 이내로만 추가 사용**하도록  
효율적으로 조정되어 있습니다.

---

**원문:**  
We have found that this significantly reduces the time to complete large MapReduce operations.  
As an example, the sort program described in Section 5.3  
takes 44% longer to complete when the backup task mechanism is disabled.

**번역:**  
실제로 이 방식은 **대규모 MapReduce 작업의 총 완료 시간을 눈에 띄게 줄이는 데 효과적**이었습니다.  
예를 들어, 5.3절에서 설명된 정렬(sort) 프로그램은  
**백업 작업 기능이 꺼져 있을 때 실행 시간이 무려 44% 더 오래 걸렸습니다.**

---
**원문:**  
**4. Refinements**  
Although the basic functionality provided by simply writing map and reduce functions is sufficient for most needs, we have found a few extensions useful. These include:

**번역:**  
**4. 기능 개선 사항 (Refinements)**  
Map 함수와 Reduce 함수만 작성하는 **기본 기능만으로도 대부분의 요구는 충족**되지만,  
실제 운영 과정에서 **유용하다고 판단된 몇 가지 확장 기능**이 있었습니다. 그 내용은 다음과 같습니다:

---

**원문:**  
• user-specified partitioning functions for determining the mapping of intermediate key values to the R reduce shards;

**번역:**  
• 중간 key 값을 R개의 리듀스 작업(R개의 shard)에 **어떻게 나눌지 사용자가 직접 정의하는 partitioning 함수**

---

**원문:**  
• ordering guarantees: Our implementation guarantees that within each of the R reduce partitions, the intermediate key/value pairs are processed in increasing key order;

**번역:**  
• 정렬 순서 보장: **각 리듀스 파티션 내에서 중간 key/value 쌍은 key 기준으로 오름차순으로 처리**된다는 보장

---

**원문:**  
• user-specified combiner functions for doing partial combination of generated intermediate values with the same key within the same map task (to reduce the amount of intermediate data that must be transferred across the network);

**번역:**  
• 동일한 키에 대한 중간 값들을 **하나의 map 작업 내에서 미리 결합(combine)하는 사용자 정의 Combiner 함수**  
→ 이렇게 하면 **네트워크를 통해 전달해야 할 중간 데이터 양을 줄일 수 있음**

---

**원문:**  
• custom input and output types, for reading new input formats and producing new output formats;

**번역:**  
• 새로운 입력 형식과 출력 형식을 지원하기 위한 **사용자 정의 입출력 타입**

---

**원문:**  
• a mode for execution on a single machine for simplifying debugging and small-scale testing.

**번역:**  
• **단일 머신에서 실행하는 모드**를 제공해, **디버깅 및 소규모 테스트를 쉽게 할 수 있음**

---

**원문:**  
**5. Performance**  
In this section, we measure the performance of MapReduce on two computations running on a large cluster of machines.

**번역:**  
**5. 성능 평가**  
이번 절에서는 **대규모 클러스터 환경에서 두 가지 작업에 대해 MapReduce의 성능을 측정**합니다.

---

**원문:**  
One computation searches through approximately one terabyte of data looking for a particular pattern.

**번역:**  
첫 번째 작업은 **약 1테라바이트의 데이터에서 특정 패턴을 탐색**하는 작업입니다.

---

**원문:**  
The other computation sorts approximately one terabyte of data.

**번역:**  
두 번째 작업은 **약 1테라바이트의 데이터를 정렬**하는 작업입니다.

---

**원문:**  
These two programs are representative of a large subset of the real programs written by users of MapReduce—

**번역:**  
이 두 프로그램은 **MapReduce 사용자들이 실제로 작성하는 많은 프로그램 유형을 대표**합니다.

---

**원문:**  
one class of programs shuffles data from one representation to another,  
and another class extracts a small amount of interesting data from a large dataset.

**번역:**  
즉, **한 부류는 데이터를 한 형태에서 다른 형태로 변환(shuffle)**하는 작업이고,  
**또 다른 부류는 방대한 데이터셋에서 중요한 정보만 추출**하는 작업입니다.

---
**원문:**  
**5.1 Cluster Configuration**  
All of the programs were executed on a cluster that consisted of approximately 1800 machines.

**번역:**  
**5.1 클러스터 구성**  
모든 프로그램은 **약 1800대의 머신으로 구성된 클러스터**에서 실행되었습니다.

---

**원문:**  
Each machine had two 2GHz Intel Xeon processors with Hyper-Threading enabled,  
4GB of memory, two 160GB IDE disks, and a gigabit Ethernet link.

**번역:**  
각 머신은 **하이퍼스레딩이 활성화된 2GHz 인텔 제온 프로세서 2개**,  
**4GB 메모리**, **160GB IDE 디스크 2개**,  
그리고 **1Gbps 이더넷 링크**를 갖추고 있었습니다.

---

**원문:**  
The machines were arranged in a two-level tree-shaped switched network  
with approximately 100-200Gbps of aggregate bandwidth available at the root.

**번역:**  
머신들은 **2단계 트리 구조의 스위칭 네트워크**로 구성되어 있었으며,  
네트워크 최상단(root)에는 **총 100~200Gbps의 대역폭**이 제공되었습니다.

---

**원문:**  
All of the machines were in the same hosting facility  
and therefore the roundtrip time between any pair of machines was less than a millisecond.

**번역:**  
모든 머신은 **동일한 데이터센터(호스팅 시설)**에 있었기 때문에,  
**어느 두 머신 간의 왕복 시간(RTT)은 1밀리초 미만**이었습니다.

---

**원문:**  
Out of the 4GB of memory, approximately 1-1.5GB was reserved by other tasks running on the cluster.

**번역:**  
총 4GB 메모리 중 약 **1~1.5GB는 클러스터에서 동작 중인 다른 작업들이 점유**하고 있었습니다.

---

**원문:**  
The programs were executed on a weekend afternoon  
when the CPUs, disks, and network were mostly idle.

**번역:**  
이 프로그램들은 **CPU, 디스크, 네트워크가 대부분 유휴 상태였던 주말 오후**에 실행되었습니다.
# HBase

HBase에 대한 개념 및 용어 정리 

---------------

1. HBase란?  
하둡 기반의 분산 데이터베이스로 빅데이터를 저장하기 위해 사용된다. HDFS위에서 작동하기 때문에 데이터 가용성과 확장성을 그대로 이용 가능하다.
noSQL에서 CAP기준으로 본다면 HBase는 CP(Consistency & partition tolerance)타입으로 볼 수 있다.  
구글의 bigTable과 유사하며 컬럼 단위로 데이터를 저장, 압축, 블룸 필터 등을 제공한다. 
기본적으로 Java API로 접근이 가능하며 추가로 REST, Avro 등을 통한 접근도 가능하다. 

2. 컬럼 패밀리란? (Column Family)  
컬럼 패밀리란 각 컬럼들 즉 row에 속해 있는 속성들이 하나의 묶음으로 되어 있는 상태를 말한다. 이러한 컬럼 패밀리가 모여서 하나의 테이블을 구성한다. 
이러한 컬럼패밀리를 사용하는 이유는 무엇인가? 
HBase는 distributed, sparse, column-oriented, versioned, non-relational의 특징을 가지고 있다.
여기서 sparse란 모든 row의 속성에 값이 있을 필요는 없음을 의미한다. 
또한 하나의 row key에 여러 데이터가 들어올 수 있으므로 이때 timestamp를 이용하여 가장 최근의 timestamp를 읽는다.

3. 리젼이란? (Region)  
리젼은 데이터를 분산으로 수평 확장 하는 기본 단위이다. 또한 테이블 데이터의 부분 집합이라고 볼 수 있다. 
리젼 서버에는 *n*개의 리젼을 가지며, 하나의 리젼은 일정 크기 이상 커지면 분리된다. 

4. HBase Master (HM)  
HM은 전체 클러스터를 관리하는 역할을 한다. 주키퍼를 이용해서 클러스터에 있는 리전 서버들을 모니터링 하고, 조정한다.
여기서 주키퍼(zookeeper)란 클러스터를 구성하는 서버들의 상태를 관리하며, 서비스들이 살아 있는지 사용 가능한지등을 모니터링한다.
주키퍼는 heartbeat를 이용해서 노드의 상태를 관리한다. 

![image](https://user-images.githubusercontent.com/36401495/104875621-11e4ae80-5999-11eb-87c6-89ea8ebe5093.png)


5. META 테이블 
META테이블은 HBase 카탈로그 테이블을 유지하며 각종 리전 위치 정보 등에 대한 데이터를 관리하며 이 테이블은 주키퍼가 관리한다. 

6. 리젼 서버 컴포넌트
WAL(Write Ahead Log): 데이터 저장 실패 복구를 위한 로그 파일이다. (RDB의 커밋 로그와 유사한 개념이다)
BlockCahce: 읽기 캐시로 자주 접근하는 데이터를 메모리에 올려놓는다.
MemStore: 쓰기 캐시로, 디스크에 쓰기 전 메모리 에서 수정되어 저장된 캐시다. 디스크에 쓰기전 정렬되며, 각 리전의 컬럼패밀리당 하나가 존재한다.

![image](https://user-images.githubusercontent.com/36401495/104875615-0a250a00-5999-11eb-9b61-370acfd6ce3d.png)

클라이언트에서 데이터와 함께 put 요청을 전송하면 WAL에 기록된다. WAL에 쌓인 데이터는 MemStore로 복사된다. 이때 MemStore는 key/value 데이터를 정렬해서 저장한다. 

7. HFile 구조
HBase는 데이터를 효율적으로 찾기 위해 multi-layed index를 사용한다. 이는 b+tree와 비슷하다. 
원래 HBase에는 primary row key에 의해 정렬된 단일 인덱스만 존재한다. -> full scan의 위험
secondary-index 를 구성하는 것은 HBase에서 보통 사용하는 방식 중에 하나다. 

---------------------
## 각종 HBase 활용 방법

1. 비트윈에서의 secondary index 구현


## Reference

https://www.joinc.co.kr/w/man/12/hadoop/hbase/about  
http://engineering.vcnc.co.kr/2014/05/hbase-schema-in-between/  (secondary-index 구현)


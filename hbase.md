# HBase

HBase에 대한 개념 및 용어 정리 

---------------

1. HBase란?  
하둡 기반의 분산 데이터베이스로 빅데이터를 저장하기 위해 사용된다. HDFS위에서 작동하기 때문에 데이터 가용성과 확장성을 그대로 이용 가능하다.
noSQL에서 CAP기준으로 본다면 HBase는 CP(Consistency & partition tolerance)타입으로 볼 수 있다.  
구글의 bigTable과 유사하며 컬럼 단위로 데이터를 저장, 압축, 블룸 필터 등을 제공한다. 
기본적으로 Java API로 접근이 가능하며 추가로 REST, Avro 등을 통한 접근도 가능하다. 

2. 컬럼 패밀리란? (Column Family)  


## Reference

https://www.joinc.co.kr/w/man/12/hadoop/hbase/about

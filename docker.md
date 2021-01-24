# Docker

도커를 실제 생성해 보고, 도커에 대한 기본적인 명령과 옵션에 대해서 정리한다. 
인프런강의를 수강하면서 실습 예제와 코드를 정리한다. 

----------

1. 도커의 등장과 배경
도커는 2013년 등장한 컨테이너 기반 가상화 도구이다. 
서버가 증가 하고 개발 환경이 복잡해 지면서 생기게 된 가상의 컨테이너라고 볼 수 있다. 
하나의 컴퓨터에서 구축한 개발 환경을 다른 개발 컴퓨터에서 동일하게 구축이 가능하도록 지원하며,
개발용 서버와 배포용 서버(dev and prod)간의 개발 환경을 편리하게 유지할 수 있도록 한다. 

이러한 도커를 알아야 하고 공부해야 하는 이유는 앞서 말한 개발의 편리성과, 컨테이너 환경에서 동작하기 때문에 동일한 플랫폼의 서로 다른 버전을 각각의 컨테이너에서 개별적으로 사용 가능하다. 

라이브러리, 버전, 패키지 설치 등 하나의 이미지로 저장할 수 있기 때문에 매번 동일한 환경을 구축해야 하는 번거로움을 줄 일 수 있다. 


2. 도커 명령어
```bash
$ docker --version   				//도커 버전
$ docker pull [image_nmae] 			//이미지 다운로드
$ docker images 					//다운로드된 이미지들
$ docker create [opt] [image_name] 	//다운로드한 이미지를 이용해 컨테이너 생생
$ dokcer run [opt] [image_name]		//컨테이너 생성 및 실행 (없으면 알아서 pull을 해서 다운을 받음)
$ docker start [container_name] 	//컨테이너 실행
$ docker restart [container_name]	//컨테이너 재실행
$ docker attach [container_name]	//컨테이너 접속
$ docker stop [container_name]		//컨테이너 정지 (컨테이너 id or name) 입력
$ docker ps 						//실행중인 컨테이너 목록
$ docker ps -a 						//종료된 컨테이너 포함 컨테이너 목록
$ docker rename [from] [to]			//컨테이너 이름 변경
$ docker rm [container_name]		//컨테이너 삭제
$ docker rmi [docker_name]          //도커 이미지 삭제
$ docker exec                       //실행중인 컨테이너에 접속할 때 
$ docker logs [container_name or id]//생성이나 실행되면서 생긴 로그 확인 (-f)와 같은 옵션을 주면 대기 하면서 어떤 로그가 생기는지 계속 확인 가능
$ docker network connect [container]//기존 생성 컨테이너에 네트워크 추가
```

주요 옵션
```
-d : detached mode 백그라운드 모드
-p : 호스트와 컨테이너 포트를 연결  (외부):(내부)
```  

```
[note]
docker run 명령어를 통해 실행 할 때, 컨테이너는 정상적으로 실행이 되어도 별다른 명령어를 주지 않으면 바로 생성되자마자 종료 하게 됨. 실행할 프로세스를 정의해 줘야함

ex) docker run ubuntu 하면 생성 되자마자 종료되지만 docker run -rm it ubuntu /bin/sh 라고 /bin/sh 라는 프로세스를 실행 시켜 주면 iterator 형식으로 실행된것을 볼 수 있음 , 여기서 rm 옵션은 프로세스를 종료시키면 자동으로 삭제 되도록 rm 옵션도 추가 하는 것을 의미함
```
-----------

# Docker 인프런 강의

1. 도커란 무엇인가?
- 2013년 에 첫 공개가 되었으며, 격리된 환경에서 작동하는 프로세스이고 리눅스 커널의 여러 기술을 활용, 이미지 단위로 프로세스 실행 환경을 구성할 수 있는 기술을 내세웠음!
- 서버를 관리한다는 것은 굉장히 어렵고, 힘든 일임.  
- 프로그램을 설치할 때 버전, 관리 등의 문제로 예상치 못한 문제들이 다양하게 생기고 서버의 환경이 매번 업그레이드 되며 또한 언어 나 플랫폼도 발전하게 됨
- 하지만? 도커의 등장으로 인해 서버관리와 개발 방식이 바뀌게 됨!!! => 컨테이너 방식 추구
- 하나의 서버에서 두개의 동일한 프로그램을 띄우는것은 꽤나 복잡하고 번거로운 일이고, 각 설정 환경에 따른 충돌이 발생할 수 있음. => config 파일, Log 등과 같은
- 전통적으로 서버 관리에서는 유저, 환경, 방화벽, 네트워크, 개발 환경, git 구축 등 일련의 과정들이 필요함
- 가상머신과의 차이점은? 가상머신 보다 빠르고, 자원 자체를 나누는게 아니라 조금더 한 단 위에서 관리 되고 있다고 봐도 됨. 가상머신 보다 더 효율적임
- 도커의 등장은 서버의 상태를 관리하기 위해 점차 발전된 방법임


- 기술적인 관점에서 보자면 가상머신 처럼 각각의 os 자체를 분리하는게 아니라 조금더 가벼움
- 각각의 플랫폼의 배포 방법의 차이를 표준화 해서 통일화 하였음!

(대충 vm과 docker 차이 그림)

- 도커의 미래? : 컨테이너의 미래는 쿠버네티스와 결합하여 더욱 확장될 것. 
- 쿠버네티스를 이용해 여러대의 서버와 여러대의 서비스를 관리하기 쉽도록 함
- 자원 관리(자원이 할당되지 않은 서버에 할당 등..), 로드 밸런싱 등


2. 도커 설치 부터 실행까지
- 도커는 기본적으로 리눅스에 실행됨. 
- docker for mac 을 이용하여 설치됨. (하지만 xhyve라는 가상머신 위에서 동작 )
- 아래처럼 명령을 하면 docker client와 docker server의 정보가 뜸. 

```bash
$ docker version
```
- docker 는 client에서 docker 관련 명령어를 입력하면 server로 이동해서 동작을 수행한 후 다시 client로 결과를 넘겨주는 역할을 함

(대충 client, server 동작 그림)




## Reference
https://www.44bits.io/ko/post/easy-deploy-with-docker  
https://www.youtube.com/watch?v=hWPv9LMlme8  
https://www.inflearn.com/course/%EB%8F%84%EC%BB%A4-%EC%9E%85%EB%AC%B8#
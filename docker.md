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
```
$ docker --version   				//도커 버전
$ docker pull [image_nmae] 			//이미지 다운로드
$ docker images 					//다운로드된 이미지들
$ docker create [opt] [image_name] 	//다운로드한 이미지를 이용해 컨테이너 생생
$ dokcer run [opt] [image_name]		//컨테이너 생성 및 실행
$ docker start [container_name] 	//컨테이너 실행
$ docker restart [container_name]	//컨테이너 재실행
$ docker attach [container_name]	//컨테이너 접속
$ docker stop [container_name]		//컨테이너 정지
$ docker ps 						//실행중인 컨테이너 목록
$ docker ps -a 						//종료된 컨테이너 포함 컨테이너 목록
$ docker rename [from] [to]			//컨테이너 이름 변경
$ docker rm [container_name]		//컨테이너 삭
```



## Reference
https://www.44bits.io/ko/post/easy-deploy-with-docker  
https://www.youtube.com/watch?v=hWPv9LMlme8  
https://www.inflearn.com/course/%EB%8F%84%EC%BB%A4-%EC%9E%85%EB%AC%B8#
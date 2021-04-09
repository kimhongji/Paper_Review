# CI(Continuous Integration) and CD(Continuous Deployment)
CI와 CD에 대해서 정리하고 현재 사용중인 GoCD에 대해서 정리한다. 

보통 CI/CD 라고 통칭되며 어플리케이션 개발 단계를 보다 자동화 하여 관리하고 쉽게 배포하고 관리할 수 있도록 도와주는 솔루션이다. 

-------------
## CI
CI는 개발자를 위한 자동화 프로세스인 지속적인 통합을 의미한다. 연결되어 있는 개발 소스에 대한 주기적인 변경을 감지하여 자동으로 통합해주며, 상호 충돌 문제를 보완한다. 
매번 개발 소스를 테스트하고 빌드하는 과정을 보다 자동화 하고 단순화 시켜주는 것이다. 

## CD
이중적으로 Delivery와 Deployment를 의미하며 지속적으로 변경된 어플리케이션 내역들을 자동으로 프로덕트 환경으로 연결할수 있도록 연결 지어주는 역할을 한다.
다음으로 deployment로 보면 이중적인 의미이지만 해당 연결된 사항을 꾸준히 배포할 수 있도록 하는 것을 의미한다. 

기존 이러한 CI/CD를 도와주기 위한 툴들이 존재한다. 젠킨스가 대표적인 관리 툴로 알려져 있다. 


## GoCD
GoCD는 젠킨스와 비슷하게 CI/CD 툴로 서버와 에이전트 관계로 구성되어 있는 툴이다. 젠킨스가 CI를 위해 만들어진것에 비해 GoCD는 CD에 조금더 초점이 맞춰져있다는
차이가 있다. GoCD 동작에는 다양한 개념들이 있다. pipeline, material, ...

 * pipline: test, build, deploy등과 같은 일련의 작업들을 정의해 둔 것
 * material: trigger 를 위한 용도라고도 생각해도 되며 소스 코드가 수정됐을때 이를 감지하여 trigger 하는 역할을 하며 pipeline에  최소 하나의 material이 있어야 한다. 

##### example
###### GoCD를 이용하여 git 소스를 원격 서버로 주기적으로 패치 하기 위해서는 어떠한 작업들을 설정해 줘야 하나? 
ㅇㄹㅇ


------------

## Ref.
* https://www.redhat.com/ko/topics/devops/what-is-ci-cd

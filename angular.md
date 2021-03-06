# Angular js

angular js에 대해서 기본적인 원리와 내용에 대해서 정리한다. 

---------------------

### 0. 용어
- 렌더링(rendering) 이란? : 서버로부터 HTML 파일을 받아 브라우져에 뿌려주는 과정이다. HTML 문서를 파싱해서 DOM 트리를 구축한다. 
CSSOM 트리를 만들면서 공통의 스타일 -> 정의 스타일 -> 인라인 스타일 순서대로 적용한다.  
- 돔(Dom) 이란? : document object model로 웹 페이지에 대한 인터페이스다. <html>, <body> 등과 같이 tree 형식으로 표현된다. 

### 1. 배경
- 자바스크립트를 보완하여 타입스크립트라고도 하 MVC/MVVM 프레임워크로 단일 페이지 웹 어플리케이션(SPA; Single Page web Application)을 제작하는데 사용된다. 
- 간단하게 MVC 패턴을 정리하면 Model/View/Controller 로, Model은 데이터, Veiw는 화면, Controller 는 Model과 View를 이어주고 관리하는 역할을 한다. 
- React나 Vue와 비교해서 차이점은?

```
React: 페이스북이 개발하고 관리하고 있는 스크립트이며 Angluar와 다르게 all-in-one은 아님
Vue: React나 Angular에 비해 상대적으로 배우기 쉬우며, 단순성과 유연성을 지니고 있지만 반면에 테스트와 디버깅에서 힘든 특징이 있음
Angular: app개발에 필요한 모든 것을 제공하기 때문에 내부 동작 방법에 대해서 특징을 알고 있어야 함, typescript기반으로 제작됨
```

그러면 Typescript란 무엇인가?  
- 

### 2. angular js는 어떻게 동작하는가

<컨트롤러 사용 예시>
- 아래 처럼 angular는 html과 통신하기 위해 {{ variable }} 과 같은 구조를 이용한다. 즉, html 자체에 데이터를 주입하지 않아야지 제대로 angular를 이용한다고 볼 수 있다. 

- 여기서 중요한 개념은 controller에 속해있는 *$scope* 이라고 하는 변수이다. scope 변수는 DOM의 현재 요소/영역을 참조하여 접근할 수 있다. 
- ng-controller 에 대입된 컨트롤러 이름과 그 내부에 속해 있는 구조들에서 해당 컨트롤러의 값들을 사용할 수 있다.


```javascript
<div ng-app="myApp">
    <div ng-controller="MainCtrl">
         {{ text }}
    </div>
</div>

...

var myApp = angular.module('myApp', []);

myApp.controller('MainCtrl', ['$scope', function ($scope) {

    $scope.text = 'Hello, Angular fanatic.';

}]);
```


<디렉티브>
- 디렉티브는 애플리케이션이 필요한 곳에 여러 번 사용할 수 있는 작은 HTML 이라고 정의되어 있고, 쉽게 DOM을 주입하거나 상호작용을 적용할 수 있다. 
- ng-* 와 같은 지시자들이 디렉티브라고 할 수 있음

<ng-click 사용 예시 및 방법>

--------

## Reference
* [1] https://medium.com/sjk5766/angular-vs-react-vs-vue-72046f6748b8

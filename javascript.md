# JavaScript

javascript에 대해서 정리한다. 기본적인 프로그래밍 관련(배열, 조건문, 루프..)은 생략하고 차이점과 특징을 위주로 정리한다. 
해당 글은 [1]과[2]의 글을 보고 다시 정리한 글이다. 


---------------
## 비동기 처리와 callback함수

비동기 처리란, 특정 연산이 끝날때까지 기다리지 않고 다른 일을 진행하는 방식을 의미한다. 예를 들어 jquery의 ```ajax```가 있다. 이러한 방식이 필요한 이유는, DB로 데이터를 요청하거나 화면에 보여지는 데이터를 찾아오려고 할 때 이를 기다리느라 다른 작업을 못하게 되는 경우에 로딩 시간이 굉장히 비효율 적으로 동작하기 때문이다. 

아래는 callback함수를 이용하여  ```ajax```의 비동기 처리 방법의 예시이다. 아래와 같이 ```$.get()```을 이용하여 ```ajax```로 데이터를 request로 받아오면 response에 해당 값이 저장이 된다. 그리고 ```callbackFunc```이라고 함수의 인자로 들어왔던 함수를 response 와 함께 호출시키게 되면 해당 ```getData``` 함수를 호출할때 해당 로직이 끝난 경우의 값을 가져오게 된다.  

###### example
```javascript
function getData(callbackFunc) {
	$.get('https://domain.com/products/1', function(response) {
		callbackFunc(response); // 서버에서 받은 데이터 response를 callbackFunc() 함수에 넘겨줌
	});
}

getData(function(tableData) {
	console.log(tableData); // $.get()의 response 값이 tableData에 전달됨
});
```
한 블로그[1]에서는 예시로, 식당에서 대기 표를 발급 받고 해당 식당에서 연락이 올때까지 쇼핑을 하고 다른 작업을 하고 있는 경우를 예시로 보였다. 여기서 식당에서 연락이 오는 것을 callback의 동작 방식이라고 볼 수 있다.   

주로 발생하는 문제중에 하나가 callback hell이라고 하는 콜백 지옥 문제가 있다. 이는 콜백함수를 연속해서 사용할때 발생하는 문제로, 아래 처럼 웹 서비스 개발중 인코딩, 사용자 인증 등의 단계를 거쳐야 하는 경우에 발생하며 좋지 않은 방식이다. 

###### example
```javascript
$.get('url', function(response) {
	parseValue(response, function(id) {
		auth(id, function(result) {
			display(result, function(text) {
				console.log(text);
			});
		});
	});
});
```


----------------
## Promise

javascript에는 Promise라는 개념이 등장한다. 이는 작업을 비동기적으로 처리할 수 있도록 하는 도구이다. 
기존 비동기 처리 방식인 ```ajax```같은것이 있는데 무슨 차이가 있나? 하고 보면 기존에는 데이터를 받아오라고 요청을 보낸 상태에서 다른 작업을 할 수 있는데, 이 때 그냥 화면에 받아온 것을 가정하고 표시를 하면 오류가 발생할 수 있다. 이를 해결하는 방법중에 하나가 Promise다. 
크게 3가지의 상태로 존재하여 ```pending```, ```resolved```, ```rejected``` 중 하나의 상태로 동작한다. 
기본 상태는  ```pending```상태이며, 동작이 수행된 이후에 각각 성공한 경우 ```resolved``` 혹은 실패한 경우 ```rejected``` 상태로 변경된다. 


###### example
```javascript
const promise = new Promise((resolve, reject) => {
  const res = true;
  // An asynchronous operation.
  if (res) {
    resolve('Resolved!');
  }
  else {
    reject(Error('Error'));
  }
});
 
promise.then((res) => console.log(res), 
           (err) => alert(err));
```

위와 같이 Promise 실행을 위해서는 내부 변수로 2개의 값을 갖는다. 각각 성공시와 실패시에 대한 결과를 보내기 위한 값이다. Promise 가 실행되면 위 예시와 같이 ```.then()``` 문법을 이용하여 결과를 받을 수 있다. 에러를 잡는 방법에는 reject로 들어온 값을 이용해서 위 예시로도 사용할 수 있지만 ```.catch()```를 이용해서도 가능하다. 

###### example
```javascript
const promise = new Promise((resolve, reject) => {  
  setTimeout(() => {
    reject(Error('Promise Rejected Unconditionally.'));
  }, 1000);
});
 
promise.then((res) => {
  console.log(value);
});
 
promise.catch((err) => {
  alert(err);
});
```

여러개의 Promise를 실행시키기 위해서는 두가지의 방법이 있는데 Promise 객체를 ```then```을 통해서 연결하는 방법이 있고, ```Promise.all()```을 이용하는 방법이 있다.
```then```을 이용했을 경우에는 순차적으로 Promise 객체에서 새로운 Promise를 return 하는 방식으로 연결되어야 한다. ```Promise.all()```을 이용하면 각각이 순차적으로 동작할 필요는 없고
각 객체가 동시에 실행되면 된다. 예시는 아래와 같다. 

###### example
```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(3);
  }, 300);
});
const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(2);
  }, 200);
});
 
Promise.all([promise1, promise2]).then((res) => {
  console.log(res[0]);
  console.log(res[1]);
});
```

----------------
## Async/Await

async와 await 방식은 기존 callback과 Promise에서의 단점을 보완하고 가독성이 좋은 프로그래밍 방법으로 등장하였다. 


-----------------
## Requests


## Reference
* [1] https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/
* [2] https://www.codecademy.com/learn/introduction-to-javascript/modules/javascript-promises/cheatsheet

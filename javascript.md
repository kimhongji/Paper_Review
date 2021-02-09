# JavaScript

javascript에 대해서 정리한다. 기본적인 프로그래밍 관련(배열, 조건문, 루프..)은 생략하고 차이점과 특징을 위주로 정리한다. 


---------------
## Promise

javascript에는 Promise라는 개념이 등장한다. 이는 작업을 비동기적으로 처리할 수 있도록 하는 도구이다. 크게 3가지의 상태로 존재하여 ```pending```, ```resolved```, ```rejected``` 중 하나의 상태로 동작한다. 
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


-----------------
## Requests

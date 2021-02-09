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
 
promise.then((res) => console.log(res), (err) => alert(err));
```


----------------
## Async/Await


-----------------
## Requests

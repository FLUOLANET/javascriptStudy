## #1 동기와 비동기

`동기적`: 위에서부터 순차적으로 하나씩 실행됨
- 한번에 한 가지 일만 할 수 있음
- 오래 걸리는 작업 한번 시작하면 끝날 때 까지 기다려야돼서 답답해 속 터짐 
 
 ```js title:Synchronous(동기적)
 console.log('1'); //1
 console.log('2'); //2
 console.log('3'); //3
```

 `비동기적`: 오래 걸리는 작업 끝날 때 까지 기다리지 않고 기다리는 동안 다음 작업 계속 처리함
- `setTimeout`은 비동기 함수
- 첫 번째 인자: 타이머 끝나면 실행할 함수(`Callback`)
- 두 번째 인자: 몇 초 타이머 할지(ms)
 
```js title:Asynchronous(비동기적)
console.log('1');

setTimeout(() => {
console.log('2');
}, 3000);

console.log('3');

//1 -> 3 -> 2
```

## #2 자바스크립트 엔진과 Web API

 브라우저 안에는 `자바스크립트 엔진`과 `Web API` 라는게 있음.
 - 일반적인 자바스크립트 코드는 `자바스크립트 엔진`에서 작동
 - 하지만 `비동기 함수`에 포함된 어떤 함수들은 `자바스크립트 엔진`이 보자마자` Web API`로 떠넘김
 - 참고) `Web API`에는 `setTimeout`, `DOM`, `Web API` 등이 있음

 `자바스크립트 엔진`이 `setTimeout` 보자마자 `비동기함수`!! 하고 `Web API`로 넘김. 그러고 `자바스크립트 엔진`은 다음 코드 실행함
 




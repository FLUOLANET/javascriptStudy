## #1 Promise가 뭐지?

- `비동기 처리`에 사용되는 자바스크립트 `객체`
-  `Result` 값과 `state`값을 포함함.
- 해당 비동기 작업의 진행 상태에 따라 
1) 진행 중:`{State: pending, Result: undefined}`
2) 성공:`{State: fulfilled, Result: 결과값}`
3) 실패:`{State: rejected, Result: Error}`

## #2 Promise 만들고 사용

```js title:Promise
// Promise 객체 만들기
const myPromise = new Promise((resolve, reject) => {
	setTimeout(() => {
		let someData = {name: 'blabla'};
		console.log('네트워크 요청 성공!!');
		resolve(someData);	
	}, 5000);
});

// 6초 뒤에 myPromise 출력 -> PromiseState: fulfilled
setTimeout(() => {
	console.log(myPromise);
}, 6000);
```

### [1] Promise 생성자 함수

1)  `Promise` 라는 이름의 `생성자 함수`로 `프로미스 객체` 만듦.
2)  인자로 `executor 함수`를 `콜백함수`로 받음. (`콜백함수`는 즉시 "정의되는 것.")
3)  `Promise 객체`가 만들어짐과 동시에, 인자로 받은 `executor 함수`가 실행됨.

### [2] Executor 함수

1)  두 개의 함수를 인자로 받음(`콜백함수`).
2)  첫 번째 인자는 `resolve`로 인식되고 두 번째 인자는 `reject`로 인식됨.
	-> 함수를 정의하고 있는 것이기 때문에 두 개의 `콜백함수` 자리에 아무 이름이나 써도 됨. 어차피 첫 번째 자리는 `resolve`, 두 번째 자리는 `reject`라는 역할을 할 함수로 인식됨. 단, 관습적으로 `resolve`, `reject`로 씀.
3)  `resolve`역할을 하는 함수를 실행하는 순간,  이 `프로미스 객체`의 `State`는 `fulfilled`로, `Result`는 `resolve`의 인자로 받은 값으로 변함.
4)  `reject`역할을 하는 함수를 실행하는 순간, 이 `프로미스 객체`의 `State`는 `rejected`로, `Result`는 `reject`의 인자로 받은 값으로 변함.

## #3 Promise 객체를 리턴하는 비동기 함수 만들기

```js title:"Promise 객체를 리턴하는 비동기 함수 만들기"
function getMoney() {
	const walletPromise = new Promise((resolve, reject) => {
		console.log('5초 뒤에 돈생김!!');
		setTimeout(() => {
			let money = 9999;
			if (money){
				console.log('9999$ 들어옴!');
				resolve(money);
			} else{
				reject(new Error('실...패....'))
			}			
		}, 5000);
	});
	return walletPromise;
}
```

 함수 마지막에 꼭 내가 만든 `프로미스 객`체 `리턴`해야됨.

## #4 만든 함수 사용(then, catch, finally)

```js title:"then, catch, finally"
getMoney()
	.then((myMoney) => {
		console.log(`잔고: ${myMoney}달러`);
	})
	.catch((error) => {
		console.log(error);
	})
	.finally(() => {
		console.log('끝!');
	})
```

### [1] then 매서드

1) `콜백함수`를 하나 받음.
2) 그 `콜백함수`는 `프로미스 객체`의 `state`가 `fulfilled`가 되면 실행됨.
3) 그 `콜백함수`는 `매개변수`를 하나 받음.
4) 그 `매개변수`는 `result` 값을 담고있음.

### [2] catch 매서드

1) `콜백함수`를 하나 받음.
2) 그 `콜백함수`는 `프로미스 객체`의 `state`가 `rejected`가 되면 실행됨.
3) 그 `콜백함수`는 `매개변수`를 하나 받음.
4) 그 `매개변수`는 `rejected`의 인자로 넣은 `Error`를 담고있음.

### [3] finally 매서드

1) `콜백함수`를 하나 받음.
2) 그 `콜백함수`는 `프로미스 객체`의 `state`가 어떤 값이 되든 가장 마지막에 실행됨.

## #5 Promise Chaining

```js title:"Promise Chaining"
const myWallet = getMoney;
myWallet()
	.then((myMoney) => {
		console.log(myMoney);
		return getMoney();
	})
	.then((myMoney) => {
		console.log(myMoney);
		return 12345;
	})
	.then((myMoney) => {
		console.log(myMoney);
	});
```

- 여러 개의 `비동기함수`를 순차적으로 실행하고 싶을 때, `Promise Chaining` 을 사용. `then`으로 계속 연결시켜서 사용할 수 있음.
- 중간에 다른 값을 리턴해도 그 값이 `프러미스`에 감싸져서 `result`만 그 값으로 변함.

## #6 Fetch API

```js title:"Fetch API"
fetch("https://jsonplaceholder.typicode.com/users")
	.then((response) => {
		return response.json()
	})
	.then((data) => {
		console.log(data);
	});
```

- `fetch API`는 특정 서버로 `네트워크 요청`을 보내는 `비동기 함수`.
- `fetch 함수`는 `프로미스`를 리턴함.
- 받아온 data를 추출하기 위해 `json 매서드` 사용.
- `json 매서드`도 `프로미스`를 반환함.
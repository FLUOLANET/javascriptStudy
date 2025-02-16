## #1 콜백함수(Callback)

`콜백함수`: 다른 함수의 인자로 전달되는 함수

```js title:Callback
// 함수를 정의할건데 인자로 콜백함수(어떤 함수) 받을거임
function anNyong(anyFunction) { 
    console.log('안녕');
    anyFunction();
}

//그 콜백함수(어떤 함수) 정의
function haSeYo() {
    console.log('하세요');
}
  
anNyong(haSeYo);
```

```js title:"Callback - Arrow 함수 버전"
const anNyong = (anyFunction) => {
	console.log('안녕');
	anyFunction();
}

const haSeYo = () => {
	console.log('하세요');
}

anNyong(haSeYo);
```

## #2 비동기 콜백

`비동기 콜백`: `비동기 처리`에 사용되는 `콜백함수`
- `비동기 작업`이 끝나고 후처리에 사용
- ex) 어떤 데이터 받아오는 작업 완료되면 그 데이터 보여줌

```js title:"이러면 원하는대로 안됨"
//2초 기다렸다가 하하하 출력하고 흐흐흐 출력하고싶음

//2초 타이머 시작하고 끝나면 하하하 출력하는 함수
function waitAndPrint() {
	setTimeout(() => {
	console.log('하하하');
	}, 2000);
}

waitAndPrint();
console.log('흐흐흐');
// waitAndPrint는 비동기함수기 때문에 2초 기다리는동안 흐흐흐부터 출력해버림
```

```js title:"잘된 예"
function waitAndSay(callback) {
	setTimeout(() => {
	console.log('하하하');
	callback();
	}, 2000);
}

waitAndSay(() => {
console.log('흐흐흐');
});
// 타이머 끝나면 하하하 출력하고 흐흐흐 출력
```

## #3 콜백지옥

- A작업 -> 3초 타이머 -> B작업 -> 3초 타이머 -> C작업 -> 3초 타이머  -> D작업 
-  이런식으로 `비동기 작업`을 여러 개 순차적으로 하려면 `콜백함수` 계속 사용해야..
   -> 코드의 가독성이 매우매우 떨어짐. 
- 이런 상황을 `콜백지옥`이라고 함.

```js title:콜백지옥
function firstTask(callback) {
	setTimeout(() => {
	console.log('첫 번째 작업 완료!');
	callback();
	}, 3000);
}

function secondTask(callback) {
	setTimeout(() => {
	console.log('두 번째 작업 완료!');
	callback();
	}, 3000);
}

function thirdTask() {
	setTimeout(() => {
	console.log('세 번째 작업 완료!');
	}, 3000);
}

firstTask(() => {
	secondTask(() => {
		thirdTask();
	})
})
```

이렇게 쓰면 나중에 유지/보수할 때 고통스러움. 
이걸 해결하는게 `Promise`
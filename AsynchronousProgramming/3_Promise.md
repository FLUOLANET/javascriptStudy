## #1 Promise가 뭐지?

- 비동기 처리에 사용되는 자바스크립트 객체
- 해당 비동기 작업의 진행 상태에 따라
1) 진행 중: {State: pending, Result: undefined}
2) 성공: {State: fulfilled, Result: 결과값}
3) 실패: {State: rejected, Result: Error}

## #2 Promise 만들고 사용

```js title:Promise
const myPromise = new Promise((resolve, reject) => {
	console.log('비동기 작업');
})
```
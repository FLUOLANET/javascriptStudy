## #1 DOM이란?

 `DOM(Document Object Model)`은 `html문서`의 각 `요소`들을 `트리`형태로 표현.
 - 개발자가 CRUD 가능
 - 하나의 개체(e.g. `<h1>`)를 `노드`라고 함.
 - 위쪽은 `부모 노드`, 아래쪽은 `자식 노드`

## #2 DOM 사용

```js title:"Basic DOM"
// <html>에 접근
document.documentElement

// <body>에 접근
document.body 

// <body>의 <style>에 접근해서 투명도 0.5로 조작
document.body.style.opacity = '0.5'; 

//someId라는 id를 가지고 있는 요소를 a에 저장
const a = document.getElementById('someId')

//p라는 태그를 전부 b에 저장 (s붙음!!)
const b = document.getElementsByTagName('p')

//someClassName이라는 클래스를 가진 요소 전부 저장
document.getElementsByClassName('someClassName')

// querySelector 사용 -> 바로 위랑 결과 같음
// querySelector 사용할 때는 css선택자처럼 사용가능
document.querySelectorAll('.someClassName')

//someId라는 id가진 요소
document.querySelector('#someId')
```

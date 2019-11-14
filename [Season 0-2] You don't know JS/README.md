# You Don't know JS

## 1회 20191102

### 공유거리

#### typeof null === 'object'

- https://2ality.com/2013/10/typeof-null.html
- [[번역]](https://github.com/FEDevelopers/tech.description/wiki/%E2%80%9Ctypeof-null%E2%80%9D%EC%9D%98-%EC%97%AD%EC%82%AC)

#### Infinity, Infinity

- https://stackoverflow.com/questions/18838301/in-javascript-why-does-zero-divided-by-zero-return-nan-but-any-other-divided-b

### 마무리

- 역할 정비
  - 일정공지(다운님)
    - 자동화가 가능하지 않을까?
  - 당일 나온 공유거리들 정리(지희님)
- 책을 다 뗀 후, PR로 후기 남겨보자

---

## 2회 20191109

### 공유거리

#### 후미콤마
> *Tip. 후미콤마를 사용했을때 장점*
>
> - diff 가 이뻐진다.
> ```javascript
> const obj = {
> a: 1
> };
>
> const obj = {
>  + a: 1,
>  + b: 2
> };
> // 2줄 수정
> ```
> ```javascript
> const obj = {
> a: 1,
> };
>
> const obj = {
> a: 1,
> + b: 2,
> };
> // 1줄 수정
> ```
​
#### RegExp()
리터럴 형식으로 사용하는것을 권한다.
​정규표현식 사용시 생성자로 사용하는것과 리터럴형식으로 사용하는것으로 코드리뷰시 의견이 나뉘었다.
(리터럴 사용시 이스케이핑 문자(`\`)가 겹치는 경우)

#### Function()
> eval()과 Function()
> https://stackoverflow.com/questions/4599857/are-eval-and-new-function-the-same-thing
> https://logical-code.tistory.com/102
​
#### Error()
```javascript
var a = new Error('2');
a.message; // '2'
```
> <https://developer.mozilla.org/en-US/docs/Web/API/Window/error_event>
> sentry (<https://sentry.io/welcome/>): 에러가 발생하는 정보를 특정 서버에 전송하여 모아 볼수있도록 하는것
​
#### 네이티브 프로토타입
```javascript
Array.isArray(Array.prototype); // true
Array.prototype.push(1,2,3);
​
var a = [1];
​
a[0] // 1
a[1] // 2 : Array.prototype을 타고올라가서 2를 가져온다.
```
```javascript
 구문을 통해 인지의 디폴트 값을 설정할 수 있다.
function isThisCool(vals, fn, rx) {
  vals = vals || Array.prototype;
  fn = fn || Function.prototype;
  rx = rx || RegExp.prototype;

  ...
}

function isThisCool(vals = [], fn = () => {}, rx = /(?:)/) {
  ...
}
```
프로토타입의 디폴트값은 수정이 불가능하다.
```javascript
Object.getOwnPropertyDescriptor(Array, 'prototype');
// configable: false
// enumerable: false
// writable: false
```
>  참고 : <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype>
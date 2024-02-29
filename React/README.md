## 새 프로젝트 만들기
`$ npx create-react-app begin-react`<br/>
`$ cd begin-react`<br/>
`$ npm start`<br/>
<br/><br/>

## 리액트 컴포넌트
**index.js**<br/><br/>
ReactDOM.render: 브라우저에 있는 실제 DOM 내부에 리액트 컴포넌트를 렌더링하겠다는 의미. id가 root인 DOM은 `index.html` 내부의
`<div id="root"></div>`에서 찾을 수 있다.

```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';

ReactDOM.render(<App />, document.getElementById('root'));

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();
```
<br/>

**Hello.js**
```
import React from 'react';

function Hello() {
  return <div>안녕하세요</div>
}

export default Hello;
```
`export default Hello;`를 해야 다른 컴포넌트에서 불러올 수 있다.<br/>
== App.js에서 `import Hello from './Hello';` 이 코드로 Hello 모듈을 불러온다.
<br/>

**App.js**
```
function App() {
  return (
    <div>
      <Hello />
      <Hello />
      <Hello />
    </div>
  );
}

export default App;
```
![image](https://github.com/wonlog/TIL/assets/149459170/365e4168-c1c0-4a1d-a03f-811bba11ae4a)

## JSX란?
![image](https://github.com/wonlog/TIL/assets/149459170/36f6c400-f1c0-4833-bb02-b70b94779e33)
1. React 구성 요소는 서로 관련되어 있기 때문에 렌더링 논리를 마크업과 함께 그룹화한다.
2. JSX는 HTML과 유사하지만 차이점이 있음을 인지한다. (변환기를 통해 학습하기)
3. 오류 메세지 확인: 마크업 수정에 대한 올바른 방향을 제시하는 오류 메세지를 확인하는 습관을 가진다.

### JSX: Putting markup into JavaScript
<기존>
웹은 HTML, CSS, JavaScript를 기반으로 구축<br/>
콘텐츠를 HTML로, 디자인을 CSS로, 로직을 JavaScript로 유지
![image](https://github.com/wonlog/TIL/assets/149459170/93f14df8-dc51-4398-ada0-c5da7501e542)

<React>
웹이 더욱 상호작용적으로 변하면서 논리가 점점 더 콘텐츠를 결정하게 됨에 따라, HTML을 Javascript에서 담당<br/>
<b>React에서 렌더링 로직과 마크업이 같은 장소, 즉 구성 요소에 함께 존재하는 이유</b><br/>
<b>This is why in React, rendering logic and markup live together in the same place—components.</b>  
  
![image](https://github.com/wonlog/TIL/assets/149459170/015fba53-6f3c-407e-9c48-f9939745875c)

각 React 구성 요소<br/>
- React가 브라우저에 렌더링하는 일부 마크업을 포함할 수 있는 JavaScript 함수
- React 구성 요소는 JSX라는 구문 확장을 사용하여 해당 마크업을 나타낸다.
<br/>

### The Rules of JSX
<b>1. Return a single root element</b>  

구성 요소에서 여러 요소를 반환하려면 단일 상위 태그로 요소를 래핑한다.
- `<div></div>`
- `<></>`
![image](https://github.com/wonlog/TIL/assets/149459170/71ba68c6-34e5-408e-b4b4-bed53e5ff9be)
![image](https://github.com/wonlog/TIL/assets/149459170/1b3d8f50-539a-42d5-a3f1-e4ded97c3312)

<b>Q. 여러 JSX 태그를 래핑해야 하는 이유는?</b>  

JSX는 HTML처럼 보이지만 내부적으로는 일반 JavaScript 객체로 변환한다. 여러 객체를 배열로 래핑하지 않고는 함수에서 객체를 반환할 수 없다.

<b>2. Close all the tags</b>  

JSX에서는 모든 태그를 명시적으로 닫아야 한다.

<b>3. camelCase most of the things!</b>  

변수 이름의 제한: 대시를 포함하거나 예약어를 사용할 수 없다.
`class`는 예약어이기 때문에 사용하지 않고 `className`을 사용한다.












```
return <div>안녕하세요</div>;
```







<br/><br/>

**Reference**
- [React 홈페이지(한국어)](https://ko.legacy.reactjs.org/)
- [벨로퍼트와 함께하는 모던 리액트](https://react.vlpt.us/)
- [BABEL: 자바스크립트의 문법을 확장해주는 도구](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&corejs=3.21&spec=false&loose=false&code_lz=DwEwlgbgfAUABHYAjKAJApgG0we2AehTgHUcAnTEAQhgPGiA&debug=false&forceAllTransforms=false&modules=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2&prettier=false&targets=&version=7.24.0&externalPlugins=&assumptions=%7B%7D)
- [convert HTML to JSX](https://transform.tools/html-to-jsx)

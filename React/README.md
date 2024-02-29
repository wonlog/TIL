## 새 프로젝트 만들기
`$ npx create-react-app begin-react`<br/>
`$ cd begin-react`<br/>
`$ npm start`<br/>
<br/><br/>

## 리액트 컴포넌트
**index.js**
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

**Hello.js**
```
import React from 'react';

function Hello() {
  return <div>안녕하세요</div>
}

export default Hello;
```
`export default Hello;`를 해야 다른 컴포넌트에서 불러올 수 있다.
== App.js에서 `import Hello from './Hello';` 이 코드로 Hello 모듈을 불러온다.

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

<br/><br/>

**Reference**
- [BABEL: 자바스크립트의 문법을 확장해주는 도구](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&corejs=3.21&spec=false&loose=false&code_lz=DwEwlgbgfAUABHYAjKAJApgG0we2AehTgHUcAnTEAQhgPGiA&debug=false&forceAllTransforms=false&modules=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2&prettier=false&targets=&version=7.24.0&externalPlugins=&assumptions=%7B%7D)

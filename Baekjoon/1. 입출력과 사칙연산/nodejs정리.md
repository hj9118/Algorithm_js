# 상황에 따른 fs 입력받는 방식
[출처](https://velog.io/@wiostz98kr/%EB%B0%B1%EC%A4%80-Node.js-fs%EB%AA%A8%EB%93%88%EB%A1%9C-%EC%9E%85%EB%A0%A5%EA%B0%92-%EB%B0%9B%EA%B8%B0)
<br/>
[node.js Docs](https://nodejs.org/api/fs.html#fsreadfilesyncpath-options)

```js
const fs=require('fs');

//1. 하나의 값을 입력받을 때
const input=fs.readFileSync('/dev/stdin').toString().trim();

//2. 공백으로 구분된 한 줄의 값들을 입력받을 때
const input=fs.readFileSync('/dev/stdin').toString().trim().split(' ');

//3. 여러 줄의 값들을 입력받을 때
const input=fs.readFileSync('/dev/stdin').toString().trim().split('\n');

//4. 첫 번째 줄에 자연수 n을 입력받고, 그 다음줄에 공백으로 구분된 n개의 값들을 입력받을 때
const input=fs.readFileSync('/dev/stdin').toString().trim().split(/\s+/);
const [n,...arr]=input; 

//5. 첫 번째 줄에 자연수 n을 입력받고, 그 다음줄부터 n개의 줄에 걸쳐 한 줄에 하나의 값을 입력받을 때
const input=fs.readFileSync('/dev/stdin').toString().trim().split('\n');
const [n,...arr]=input;
```
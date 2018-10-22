### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```
```js
function insensitiveEqual(str1, str2){
  if(str1.toLowerCase() === str2.toLowerCase()){
    //모든 문자열을 같은 타입으로 바꿔준다. 소문자나 대문자로.. 비교.
    return true
  } else {
    return false
  }
}
```

```js

function insensitiveEqual(str1, str2){
  return str1.toLowerCase() === str2.toLowerCase()
}
```

```js
const x = 'hello'.toUpperCase();
const y = 'world'.toUpperCase();

if (x === y) {
  console.log(true)
} else {
  console.log(false)
}

function insensitiveEqual(str1, str2) {
   str1=str1.toUpperCase();
   str2=str2.toUpperCase();
   if (str1 === str2){
     return true
   } else {
     return false
   }
}
```


### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```


```js
function leftPad(s, n) {
  if (s.length < n) {
    return s.padStart(n, ' ')
    // 글자 길이를 출력되는 자연수만큼 맞추는 문제 이므로, padStart 메소드를 이용하여 왼쪽에 자연수를 넣어주고, 오른쪽에 공백 넣어준다.
  } else {
    return s
  }
}
```

```js
function leftPad(s, n) {
  if (s.length < n) {
    //s의 길이가 n보다 작으면..
    const spaceNum = n - s.length
    //공백숫자를 구해준다. 큰 자연수 - 글자길이.
    return ' '.repeat(spaceNum) + s
    //space 한칸을 공백숫자만큼의 repeat으로 채워주고 그다음 글자.
  } else {
    return s
  }
}
```

### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

```js

function count(str) {
  let num = 0
  //숫자 셀거야.
  for (let i = 0; i < str.length; i++) {
    //문자열 만큼의 숫자
    if (str[i] === 'a' || str[i] === 'e' || str[i] === 'i' || str[i] === 'o' || str[i] === 'u') {
      // 문자열하나하나보면서 a,e,i,o,u를 찾는다.
     num += 1
     //모음의 숫자를 세는데 0부터가 아니라 1부터 센다.
    }
  }
  return num
  //문자에 대한 숫자를 반환한다.
}

```



### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```

```js

function countChar(input) {
  const obj = {};
  for (let i = 0; i < input.length; i++) {
    const char = input[i]
    if (!(char in obj)){
      //글자를 본적이 없다면
      obj[char] = 1
      //"글자" : 1 을 적어준다.
    } else {
      obj[char]++
      //글자를 본적이 있다면 갯수를 1 증가 시켜준다.
    }
  }
  return obj
}
```


### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)

```js
function isPalindrome(input) {
  arr = input.split('');
  //문자열을 특정문자를 기준으로 잘라 새배열 생성
  num = arr.length
  //글자
  for (i=0; i<num; i++){
    if(arr[i] === arr[num-i-1]) {
      continue;
    } else {
      return false;
    }
  }
    return true;
}

isPalindrome('토마토마토') // true;
isPalindrome('토마토바토') // false;
```

```js
function isPalirome(input){
  for(let i = 0; i < input.length; i++){
    const left = i;
    const right = input.length - 1 -i;
    //글자길이에서 0부터 시작하는 1 빼고 마지막 글자 i빼기.
    if(input[left] !== input[right]){
      //앞글자랑 뒷글자랑 같니 ?
      return false;
    }
      return true;
  }
}
```


### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```

```js
function subString(str){
  let subWord = new Array()
  let cnt = 0
  for(let i = 0; i<str.length; i++){
    for(let j = i+1; j<=str.length; j++){
      subWord[cnt++] = str.slice(i,j);
    }
  }
  return subWord
}
subString('아메리카노')
```

### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```

```js
function removeDuplicates(str) {
  let memory = '';
  //새로운 문자열을 넣을 곳을 마련해준당.
  for (let i = 0; i < str.length; i++) {
    //입력받은 문자열을 살펴본다.
    if (!memory.includes(str[i])) {
      memory += str[i];
      //새로운 문자열 넣으라고 한 변수에 만약 지금 내가 보고있는 문자열을 본적이 없으면,
      //넣어주라고 말해준다.
    }
  }
  console.log(memory);
}

removeDuplicates('tomato') // 'toma'
```

### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.

```js
function removeId(input){
 let seen = false;
 let memory = ' ';
 for (let i = 0; i < input.length; i++){
   // 내가 지금 보고 있는 글자가 ‘@’이면
   // seen의 값을 true로 바꾼다
   if (input[i] === '@'){
     seen = true;
   } if (seen === true){
     memory += input[i];
   } else{
     memory += '*';
   }
   // seen이 true이면
   // 내가 지금 보고 있는 글자 그대로 memory에 덧붙인다
   // 아니면, 별표를 대신 덧붙인다.
 }
 return memory;
 // 변환한 결과를 반환한다.
}
removeId('keoeke@gmail.com');
```

- `split` 메소드를 이용해서 풀어보세요.

```js
function removeId(input) {
  const strings = input.split('@');
  //매개변수 .split('@')메소드로 골뱅이 앞 뒤로 잘라서 배열(두 부분 나옴)로 만듬
  let memory = '';
  //값을 담을 저장공간을 마련해준당.
  for (let i = 0; i < strings[0].length; i++) {
    //for문 돌리는데 별표 추가해 줄 부분은 배열 인덱스 0번째니까 범위를 걔까지라고 정해줌
    memory += '*';
  }
  return memory + '@' + strings[1];
  //반환할 때 새롭게 생성된 애랑 + @ + 두번째 배열 합
}

removeId('hello@gmail.com'); // 반환값 : *****@gmail.com
```
- 짧은코드

```js
const removeId2 = (input) => {
  // '@'을 기준으로 쪼갠 후
  const splitted = input.split('@')
  // id 부분과 같은 길이를 갖는 별표 문자열을 만든다.
  const stars = '*'.repeat(splitted[0].length)
  // 별표를 @, 도메인 부분과 이어붙인 후 반환한다.
  return stars + '@' + splitted[1]
}
```



### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.

### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

### 문제 11

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

### 문제 12

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.

### 문제 13

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

### 문제 15

`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```

### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```

### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```

# 김영민 [201840113]
## [06월 01일]
## 버전에 따른 코드 사용 여부
IE -> var<br>
최신 웹 브라우저 -> let, const<br>
var를 사용해도 오류는 생기지 않는다<br>
그냥 let을 쓰면될듯??<br>
<hr>

## 객체 모델
screen 객체
웹 브라우저 화면이 아니라 웹 브라우저 그 자체이다.
<pre>
<code>
width() -> 화면의 너비<br>
heigth() -> 화면의 높이<br>
availWidth()-> 실제 화면에서 사용 가능한 너비<br>
availHeigth()-> 실제 화면에서 사용 가능한 높이
등등
</code>
</pre>
<hr>

## JQuery
<pre>
<code>
Basic<
$(value1).method(parameter1, parameter2);
//css 선택자

$('h1') -> h1 태그를 선택한다.
$('h1.logo') -> h1 태그 중 logo 클래스를 선택한다.
$('h1#logo') -> h1 태그 중 logo 아이디를 선택한다.

//each()
$('h1').each(function (index, item){
});
odd, even 선택자
odd -> 홀수번째 선택자 even -> 짝수번째 선택자
</code>
</pre>
<hr>

## 문서 객체 조작
text() -> html 태그 내부의 문자를 조작한다.
html() -> html 태그 내부의 문자를 조작하면서 html를 인식한다.
<pre>
<code>
$('document').ready(function (){
alert($('p').text());
alert($('p').html()); })

text() -> 모든 p 태그 내부 문자를 출력 html() -> 첫 번째로 선택된 p 태그 문자를 출력
</code>
</pre>
<hr>

## 스타일 조작
<pre>
<code>
css() -> 스타일을 조작한다.

$('html').css({
    color : 'blue',
    backgroundColor : 'white',
})
JSON 형식으로도 사용 가능하다.
</code>
</pre>
<hr>

## 이벤트
<pre>
<code>
on() -> 이벤트를 연결한다.
off() -> 이벤트를 제거한다.

//이벤트 직접 연결

$('선택자').on(<이벤트이름>, <콜백함수>);
</code>
</pre>
<hr>

## 애니메이션
<pre>
<code>
animate() -> 애니메이션을 적용한다.

//애니메이션 연결

$('선택자').animate(<속성>, <시간>, <콜백함수>);
</code>
</pre>
<hr>

### [05월 25일]
## express 모듈
express 모듈은 웹 서버를 개발하는 모듈이다.<br>

$ npm install express : 입력하면 express 모듈을 설치할 수 있다.

Express 모듈의 메소드
<pre>
<code>
express() : 서버 애플리케이션 객체를 생성합니다.
app.use() : 요청이 왔을 때, 실행할 함수를 지정합니다.
app.listen() : 서버를 실행합니다.
// 모듈을 추출합니다.
const express = require('express');

// 서버를 생성합니다.
const app = express();

// request 이벤트 리스너를 설정합니다.
app.use((request.response) => {
    response.send('<h1>Hello express</h1>');
});

// 서버를 실행합니다.
app.listen(52273, () => {
    console.log('Server running at http://127.0.0.1:52273');
});
</code>
</pre>
<hr>

## 페이지 라우팅
페이지 라우팅이란 클라이언트 한테 적절한 페이지를 제공하는 기술이다.<br>

Express 모듈의 페이지 라우팅 메소드
<pre>
<code>
get(path,callback) : GET 요청이 왔을 때 발생했을 때 이벤트 리스너를 지정합니다.
post(path,callback) : POST 요청이 왔을 때 발생했을 때 이벤트 리스너를 지정합니다.
put(path,callback) : PUT 요청이 왔을 때 발생했을 때 이벤트 리스너를 지정합니다.
delete(path,callback) : DELETE 요청이 왔을 때 발생했을 때 이벤트 리스너를 지정합니다.
all(path,callback) : 모든 요청이 왔을 때 발생했을 때 이벤트 리스너를 지정합니다.
</code>
</pre>
<hr>


## response 객체
response 객체의 메소드

<pre>
<code>
send() : 데이터 본문을 제공합니다.
status() : 상태 코드를 제공합니다.
set() : 헤더를 설정합니다.
send() 메소드는 사용자에게 데이터 본문을 제공합니다. 또한 가장 마지막에 실행해야 하며, 두번 실행할 수는 없습니다.
</code>
</pre>
<hr>

## Content-type
Content-type은 클라이언트로 제공되는 데이터의 형태입니다. text, html, png, mpe, json 등 여러가지가 존재합니다.<br>
type() 메소드로 Content-type을 MIME 형식으로 지정할 수 있습니다.
<pre>
<code>
app.get('/image',(request, response) => {
    fs.readFile('image.png',(error,data) => {
        response.type('image/png');
        response.send(data);
    });
});
</code>
</pre>
<hr>

## request 객체
request 객체는 요청에 해당하는 객체를 말합니다. 즉, 클라이언트가 입력한 값들도 요청에 해당합니다.
<hr>

## 미들 웨어
익스프레스에서의 미들웨어는 클라이언트와 서버 사이에서 요청과 응답을 조율하고 관리하는 주체이다. 미들웨어는 요청과 응답을 조작하여 기능을 추가하기도 하고, 나쁜 요청을 걸러내기도 함.


## morgan 미들웨어
morgan은 express의 미들웨어로 사용할 수 있는 외부 모듈이다. 또한 morgan은 로그 출력 미들웨어로써, 웹 요청과 관련된 내용을 출력하는 미들웨어이다.

6-2. body-parser 미들웨어
body-parser 미들웨어는 요청 본문을 분석하는 미들웨어이다. body-parser은 URL 쿼리에 정보를 담아 전송하는 과정에서 클라이언트가 어떤 형태의 Encoding-type으로 요청했는지 확인하는 것을 쉽게 처리한다. 이를 사용하지 않으면 복잡하게 처리한다. 즉 body-parser 미들 웨어는 put과 post 방식으로 요청된 request.body를 쉽게 분석할 수 있다.
<hr>

## 05월 18일
## process 객체의 속성과 이벤트
Node.js 는 process 전역 객체를 제공
process 객체는 프로세스 정보를 제공하며 제어할수있게하는 객체

progress객체의 속성
<pre>
<code>
env = 컴퓨터 환경정보
version = 버전을 나타냄
versions = 종속된 프로그램 버전
arch = 프로세서의 아키텍처를 나타냄
platform=  플랫폼을 나타냄
</code>
</pre>
process 객체의 메소드
<pre>
<code>
exit 프로그램종료
memoryUsage() 메모리 사용정보 객체를 리턴
uptime() 현재 프로그램이 실행된 시간을 리턴
</code>
</pre>
<hr>

## 전역변수
__filename = 현재실행중인 코드의 파일 경로
__dirname = 현재 실행중인 코드의 풀더 경로
<pre>
<code>
console.log(__filename);
console.log(__dirname);
</code>
</pre>
<hr>

## url 모듈
const url =require'(url')
메소드
<pre>
<code>
resolve(from to) 매개변수를 조합하여 완전한 url문자열을 생성해 리턴
parse(urlStar) : URL 문자열을 URL 객체로 변환해 리턴
format(urlObj) : URL 객체를 URL 문자열로 리턴.
resolve(from,to) : 매개 변수를 조합하여 완전한 URL 문자열을 생성해 리턴
</code>
</pre>
<hr>

## File System 모듈
const fs = requrie('fs')
파일 읽기 : 실행할 자바스크립트 파일이 있는 풀더에 textfile.txt이름의 파일을 생성
fs.readFileSync(<파일이름>) = 동기적으로 파읽을 읽는다
fs.readFile(<파일이름>,<콜백함수>) 비동기적으로 파일을 읽는다
<hr>

## 노드 패키지 매니저
Node.js는 npm 패키지 매니저를 사용해서 외부모듈을 설치가능함
예) npm istall <모듈이름>
npm istall express @사용으로 원하는 버전을설치 할수있다
express@4
<hr>


## [05월 11일]
### 예외처리
프로그램 실행시 문제가 발생하면 프로그램이 자동으로 종료되는데 이렇게 발생한 오류를 예외라고 한다
<br>
<br>
## try catch 구문
<pre>
<code>
try {
    // 예외가 발생하면
}catch (exception) {
    // 여기를 실행
}finally{
    // 여기는 무조건 실행
}
</code>
</pre>

예외 강제처리
<pre>
<code>
throw '강제예외';       //throw 뒤에 문자열 또는 Error 객체 입력 
</code>
</pre>

<hr>

### Array 객체
<pre>
<code>
concat()    //매개 변수로 입력한 배열의 요소를 모두 합쳐 배열을 만들어 리턴
join()      //배열안에 모든 요소를 문자열로 만들어 리턴
pop()       //배열안에 마지막 요소를 제거하고 리턴
push()      //배열의 마지막에 새로운 요소를 추가
reverse()   //배열의 순서를 뒤집음
slice()     //배열의 지정한 부분을 리턴
sort()      //배열의 요소를 정렬
splice()    //배열요소의 지정한 부분을 요소를 리턴
</code>
</pre>
<hr>

### Date 객체
Date객체 생성법
<pre>
<code>
1. new Date()   //현재시간으로 객체생성
2. new Date(유닉스타임)     //유닉스 타임으로 객체생성 
3. new Date(시간문자열)     //문자열로 객체생성
4. new Date(<년>, <월>, <일>, <시간>, <분>, <초>, <밀리초>) // 시간 요소를 기반으로 객체생성
</code>
</pre>


## [05월 04일]
## 객체 자료형
기본 자료형 : 자바스크립트에서 기본 제공하는 여섯자료중 3개(숫자,문자열,불)
### Number 객체
생성방법
<pre>
<code>
let number = 273;
let number = new Number(273);
</code>
</pre>
number 생성자 함수의 속성
>MAX_VALUE = 숫자가 나타낼수있는 최대숫자<br>
MIN_VALUE = 숫자가 나타낼수있는 최소숫자<br>
NaN = 숫자로 나타낼수 없는숫자<br>
POSITIVE_INFINITY = 양의 무한대 숫자<br>
NEGATIVE_INFINITY = 음의 무한대 숫자
<hr>

### String 객체
생성방법
<pre>
<code>
let string = '안녕하세요';
let string = new String('안녕하세요');
</code>
</pre>
String 생성자의 속성
>length = 준자열의 길이를 나타냄
<hr>


## 생성자함수
생성자함수 : 객체를 만드는 함수, 대문자로 시작되는 이름을 가진다<br>
프로토타입 : 생성자 함수로 만든 객체는 프로토타입이라는 공간에 지정하여
모든객체가 공유하도록 사용가능하다
<pre>
<code>
function Pruduct(name, price){
    this.name = name;
    this.price = price;
}
</code>
</pre>
<hr>

## 속성과 메서드
배열의 요소처럼 객체의 속성에도 다양한 자료형이 입력가능하다<br>
**메소드 : 객체의 속성중 자료형이 함수인경우**
<pre>
<code>
var object: {
    number: '546',
    string: 'KimSeungGeun',
    bloolean: true,
    array: [1,2,3,4,5],
    method: function() {
        console.log("케인인님 한판해요")
    }
} 
</code>
</pre>

<hr>

## 객체
여러개의 자료형을 한번에 저장하는 자료형<br>
객체의 선언 방법
<pre>
<code>
let product ={
    제품명: '애플망고',
    유형: '당절임',
    성분: '망고, 설탕, 나트륨, 색소',
    원산지: '필리핀'
}      
                  // 제품명,유형,성분,원산지를 가진 객체 product 생성

console.log(product);    // product 객체출력
</code>
</pre>
객체명['속성이름']  = 속성에만 따로 접근가능<br>
객체명.속성이름  = 속성에만 따로 접근가능
<hr>

## [04월 27일]
## 배열
let array = ['사과','사과' , '사과', '사과'];

## 콜백함수
function callTenTimes(callback) {
    for (let i = 0; i< 10; i++>){
        callback();
    }
}
## 함수의 기본형태
function <함수이름>(<매개변수>) {
    <함수 코드>
    return <리턴값>
}

## 함수 사용법
익명함수
let <함수이름> = function () {};

선억적함수
function <함수이름> {}

화살표 함수 (중요!!)
let 함수 = () => {
    console.log(함수 첫째줄);
    console.log(함수 첫째줄); 
};

함수(); // 함수호출
## [04월 6일]
### continue문
반복문 내부에서 형재반복을 멈추고 다음반복을 진행한다

### break문
switch 문 또는 반복문을 빠져 나올때 사용한다
무한반복문은 break문을 사용해여 빠져나올수있다.

### 중첩반복문
for문을 두개이상 반복하여 사용한다
for (----){
    for (----){
    }
}
### for in 반복문과 for of 반복문
객체에 쉽게 적용할때 사용한다
for (let 인덱스 in 배열){

} 
for (let 요소 of 배열){

} 
사용법은 for문과 같다
## [03월 30일]

### switch 문
괄호 안에값을 비교, break로 반복문을 빠져나감
break;
if문과 switch중 알아서 선택해서 잘쓰자

### 삼항연산자
<불 표현식 ? <참> : <거짓>>
자바의경우 해당 변수가 undefined인지 확인할때 자주사용
한줄로 사용할수 있을때만 사용

### 짧은 초기화 조건문
'삼항연산자를 활용한 변수초기화' 코드를 더짧게 적는방법
● A||B에서 A가 참이라면 A로 대체
● A||B에서 A가 거짓이라면 B로 대체

### 배열
여러개의 자료를 한번에 다룰수있는 자료형
EX) let 이름 = [..., ..., ..., ..., ...]

### while 반복문
가장기본적인 반복문, if와 비슷하지만 조건문이 참이면 중괄호안에 문장을 계속 시행한다
ex) while (true){
    console.log("무한반복);
}

### for 반복문
반복문이다
ex) for (let i = 0; i < 반복횟수; i++>){
}






## [03월 23일]
논리 연산자
! = 부정 연산자
참을 부정으로 부정을 참으로 바꾼다
ex)
console.log(!true);      false
console.log(!false);      true
console.log(!(123>13))   false
console.log(!(123<12))   true

|| =  논리합 연산자
둘중 하나만 참이라도 참
ex)
true true = true
true false = true
false true = true
false false = false

&&   논리곱 연산자
둘중 하나만 false면 false
ex)
true true = true
true false = false
false true = false
false false = false

변수

1.변수 선언   선언 = let,const
2.변수에 값을 할당

변수에 값을 저장하는것 = 변수에 값을 할당
변수를 선언한 후 처음 값을 할당 = 변수를 초기화
보통 선언과 초기화는 한번에 처리

js는 다른 언어와 다르게 변수에 자료형을 지정하지않음
= int 나 string처럼 값을 따로 주지않아도 됨
근데 에러가 잘나오니 그냥 값을 넣으삼



증감 변산자

변수++   값에 1을 더함
++변수    값이 나오고 1을더함
변수--   값에 1을 뺌
--변수   값이 나오고 1을 뺌

복합 대입 연산자
+= 숫자 덧셈 후 대입 연산자
-= 숫자 뺄셈 후 대입 연산자
*= 숫자 곱셈 후 대입 연산자
/= 숫자 나눗셈 후 대입 연산자

자료형 검사

typeof    해당 변수의 자료형을 추출(자료형을 확인할때)
키워드이면서 연산자
int      숫자
string      문자열
boolean      참/불
function      함수
object      객체
underfined   초기화되지 않은 것을 표현하는 자료형
ex)
typeof(1)
'int'
typeof(true)
'boolean'

강제 자료형 변환

Number()      숫자형자료형으로 변환
String()      문자열로 자료형 변환
Boolean      불로 자료형 변환

Number()함수와 NaN
ex)
console.log(Number("52"));      52
console.log(Number(52.123"));   52.123
console.log(Number(true));      1
console.log(Number(false));      0
console.log(Number("안녕하세요"));   NaN

NaN(Not a Number) 
숫자 자료형이지만 숫자가 아닌것
NaN은 무조건적으로 다름
NaN인지 확인할때는isNaN()함수를 사용

Boolean()함수
0,NaN,""(빈문자열),null,underfined 이외는 모두 true로 치환

자동자료형 변환
숫자와 문자열에 + 연산자를 적용하면 자동으로 숫자가 문자열로 변환

일치연산자
===   자료형과 값이 같은지 비교함(int와 string이면 false)
!==   자료형과 값이 다른지 비교함

상수

let    변수를 바꿀수 잇음
const   변수 못바꿈
일단 상수(const)를 사용하고 오류가 발생하면 변수(let)로 교체

if조건문

표현식이 true면 을 실행, false면 실행안함
조건문을 만족해 실행되는 문장이 한 행이면 중괄호 생략가능
여러행이라면 중괄호로 감싸야함

if else 조건문
조건이 아니면 else문으로 이동
두가지로 분명하게 나뉘는 상황에서 편리하게 사용할 수 있다

중첩 조건문
조건문 안에 조건문을 중첩해 사용하는것
여러번 중첩 가능

if else if 조건문

중첩 조건문의 중관호를 생략했을 때 만든 조건문
중복되지 않는 세가지 이상의 조건을 구분할때 사용
## [03월 16일]
자바스크립트의 발전
    세계에서 가장 오해를 많이 받는 프로그래밍 언어
        부수적인 프로그래밍 언어로 취급
    풍부한 경험을 제공하는 인터넷 애플리케이션(RIA)
        • RIA : 풍부한 경험을 선사하는 웹 애플리케이션

Node.js
    • 2008년 9월 : 구글은 크롬 웹 브라우저의 베타 버전을 발표
    • 2009년 1월 이후 : 자바스크립트를 웹 브라우저가 아닌 곳에서도 사용할 수 있는 표준안 제시
    • CommonJS 표준 발표 이후 : CommonJS 표준과 V8 자바스크립트 엔진을 기반으로 Node.js를 개발

스레드 
    비동기 방식의 장보기를 프로그래밍 언어로 구현하는 방법

Node.js기 기반의 프로그램을 만들 수 있도록 설계되어 초보자도 쉽게 프
    모든 모듈(라이브러리)이 처음부터 비동로그램을 만들 수 있음

자바 스크립트로 하는일
    모바일 애플리케이션 개발
    데스크톱 애플리케이션 개발
    게임 개발 (유니티 등)
    데이터베이스 관리

자바의 기본용어
    식별자 : 이름을 붙일때 사용하는 단어, 함수의 이름등으로 사용

숫자 
    가장 기본적인 자료형
    숫자 생성 = console.log(52)
    사칙 연산자 +, -, *, /
    나머지 연산자 = %

문자열
    문자의 집합
    문자열 생성시 큰따옴표나 작은따옴표 사용

    이스케이프 문자 
        \t = 수평탭
        \n = 줄바꿈
        \' = 작은따옴표
        \" = 큰따옴표
        \\ = 역슬래시
        
 

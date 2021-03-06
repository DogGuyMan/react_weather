# Weather Project
#### [배포 사이트](https://dogguyman.github.io/react_weather/) : https://dogguyman.github.io/react_weather/

## 목차
1. ##### [기획 문서](#weather-project-요구-분석서)
2. ##### [시스템 설계](#weather-project-시스템-설계)

---

# Weather Project 기획 문서

## 목차
[1. 개요](#1-개요)
[2. 기능적목표](#2-기능적-목표)
[3. 요구,제약사항](#3-제약-사항)

---

### 1. 개요
* 접속한 기기 (모바일, PC) 플랫폼들의 위치에 따라 현재 날씨의 정보를 시각적이고 심미적으로 제공하는 것이 주목표입니다.

### 2. 기능적 목표

#### 2-1 자료 흐름도
* **1. 최상위** 
  * ![](2022-04-25-05-53-30.png)

* **2.위도 경도 위치탐색**
  * ![](2022-04-25-05-56-51.png)
	* input : 팝업 허용
	* output : latitude longitude

* **3.날씨 정보 얻기**
  * ![](2022-04-25-06-02-04.png)
  * input : latitude longitude
  * output : weather Json

#### 2-2 기능 
1. 아이콘 : 날씨와 시간 따라 각기 다른 아이콘
	* 디자인 툴 : clip Studio ,Figma, Zeplin
2. 배경 : 날씨와 시간 따라 각기 다른 아이콘
	* 저녁에 가까워질수록 점점 어두워지기
	* 구름이 많아질수록 배경이 점점 채도 감소(탁해짐)
3. 수치적 정보 : 온도, 시간
	* 아이콘 밑에 온도 표시
	* 좌측 상단에 현재 시각 출력
4. 위치 정보 : (도/시/군/구/동/읍/면/리)
	* 위치 정보는 영어 표기

### 3. 제약 사항
- Client
  - 1. 웹 브라우저 사용 가능환경
  - 2. 모바일 & PC 해상도 사용환경

---

# Weather Project 시스템 설계

## 목차
[1. 개요](#dev-tech)
[2. 시스템 구조](#2-시스템-구조도)
[3. 모듈설계](#3-모듈-설계)
[4. UI 설계](#4-ui-설계)

---

## 1. 개요
* ### Dev Tech
    1. React
    2. Typescript
    3. Scss
    4. Node.js
    5. Github

## 2. 시스템 구조도
![](2022-04-25-06-23-27.png)

## 3. 모듈 설계
* ### 사용 모듈
  * API
    1. geoLocation
    2. openWeather
  * Import
    1. react-live-clock
    2. loading
    3. weather
    4. setBackground
    5. setEllipse
    6. web-vitals

* ### API
  * #### 1. geoLocation API
    |모듈|설명|
    |:--|:--|
    |모듈이름|naviagtor.geoLocation|
    |기능|현재 기기의 위치를 Object로 가져옵니다|
    |output|Geographic coordinate : {<br> - response.coors.latitude<br> - response.coors.longitude<br>}|

  * #### 2. openWeather API
    |모듈|설명|
    |:--|:--|
    |모듈이름|openWeather|
    |기능|geoLocation의 위도 경도의 기상정보를 가져옵니다|
    |output|{<br>"weather":[...]<br>"wind":{...}<br>"name" : "City Name"<br>}|

---

* ### Import
    * #### 1.react-live-clock
        |모듈|설명|
        |:--|:--|
        |모듈이름|react-live-clock|
        |기능|timezone 위치에 따른 시간 출력합니다|

    * #### 2. Loading
        |모듈|설명|
        |:--|:--|
        |모듈이름|Loading|
        |기능|geoLocation 접근 허락 유무에 따라<br>Loading Page와 Error Page 그리기<br>OpenWeather API가 Response 되었다면<br> 기상정보에 따라 Weather Page 그리기 |
        |오류|someError : geoLocation 접근 거부|
        |멤버 변수|isLoaded: false (API Response 유무 Boolean) <br>error : null : (에러 String) <br>temperature : null : (온도 Number)<br>name:null : (기상정보 : 구름, 비, 눈)<br>curLocation : null (현재 위치 String)<br>|
        |매서드|componentDidMount() : state의 업데이트 조건을 작성.<br>_getWeather(lat, long) : openWeather API fetch후 state 초기화|

    * #### 3. Weather
        |모듈|설명|
        |:--|:--|
        |모듈이름|Weather|
        |기능|Weather호출시 Prop에들어간 값을 가지고 Weather Page의 UI를 그립니다.|
        |멤버 변수|weatherCases : (String Key로 각 기상상테에 따라서 입력되는 정보 처리 <br>ex). title텍스트, subtitle, image Icon)|
        |함수|Weather(temperature : number, name : string, curLocation : string)|

    * #### 4. setBackground
        |모듈|설명|
        |:--|:--|
        |모듈이름|setBackground|
        |기능|기상 정보를 입력받고 그에 따라 배경의 색을 다양하게 그린다.|
        |멤버 변수|weatherCasesBG : (String Key로 기상 정보 style class에 접근한다) |
        |함수|Background(name:string)|
    * #### 5. setEllipse
        |모듈|설명|
        |:--|:--|
        |모듈이름|setEllipse|
        |기능|기상 정보를 입력받고 그에 따라 언덕(타원 배경)의 색을 다양하게 그립니다.|
        |멤버 변수|weatherCasesE : (String Key로 기상 정보 style class에 접근한다) |
        |함수|Ellipse(name:string)|

 
### 4. UI 설계
#### 1. Create Icon with Clip Studio
![](2022-04-25-06-14-44.png)

#### 2. Create weather_from with Figma
![](2022-04-25-06-11-42.png)
![](2022-04-25-06-17-33.png)
* openWeather의 아이콘과 1대1 대응하여 새로운 아이콘 만들었습니다.

#### 3. Convert Css From with zeplin
![](2022-04-25-06-16-22.png)

---

## Result
### 1. PC
![](2022-04-25-06-39-39.png)

### 2. Mobile
![](2022-04-25-06-40-12.png)

---

## 참고
1. [소프트웨어 SW 설계 문서](https://cs.kangwon.ac.kr/~ysmoon/courses/2009_2/se/project/7.design-report.pdf)
2. [리액트 깃허브 배포법](https://velog.io/@byjihye/react-github-pages)

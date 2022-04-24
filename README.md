https://cs.kangwon.ac.kr/~ysmoon/courses/2009_2/se/project/7.design-report.pdf

# Weather Project 요구 분석서

---

## 목차
[1. 개요]()
[2. 기능적목표]()
[3. 요구,제약사항]()
[4. 인수조건]()

---

### 1. 개요
날씨와 관련된 다양한 정보를 볼 수 있는 웹사이트 제작

### 2. 기능적 목표

```
---엔트리---

if(위치정보()){
//있음
서비스 실행(위치정보)
}
else{
//
서비스 없음
}
```

위치정보 Geolocation 사용

```
---서비스---

서비스_실행(_위치) {
JSON = API(_위치);
기상상태 비 눈 극한
온도
습도
바람
강우량
도시이름

}

```

openweather 사용

### 3. 조건

지역 날씨에 따라 뒷 이미지와 표시가 달라진다.

확장이 간편하게 만들기

---

# Weather Project 시스템 설계

---

## 목차
[1. 개요]()
[2. 시스템 구조]()
[3. 모듈설계]()
[4. UI 설계]()

---

## 1. 개요

1. 주요 기능
1. 현재 위치 반환
2. 날씨 정보 반환

## 2. 시스템 구조
```
위치 가져오기
위치에 대한 날씨 가져오기
```

## 3. 모듈 설계

---

|모듈1|설명|
|:--|:--|
|모듈이름|엔트리|
|기능|시스템 실행 유무를 가지고 |
|오류||
|멤버자료||
|메서드||
|인풋||

---

|모듈1|설명|
|:--|:--|
|모듈이름|API 처리|
|기능|API처리를 통해 UI 그려주는 역할|
|오류||
|멤버자료|JSON / 컴포넌트|
|메서드||
|인풋|지오 로케이션|

---

|모듈1|설명|
|:--|:--|
|모듈이름|컴포넌트 처리|
|기능|JSON을 입력받아 컴포넌트 생성|
|오류||
|멤버자료||
|메서드||
|인풋|JSON|

---
### 수정
app 을 수정하자
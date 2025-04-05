
# 📌 임베디드통신시스템 5주차 과제1

## 📖 소개

[임베디드통신시스템]강의의 5주차 첫 번째 과제로 라즈베리 파이와 GPIO를 이용하여 LED를 제어하는 시스템을 만들어보았습니다. 

## 과제 설명

![이미지 설명](image/assignment_description.png)

1. domino 폴더 만들기
2. domino 폴더 안에 domino4라는 source파일 만들기
3. domino4 파일 내용 편집하기 
4. 라즈베리 파이와 브레드 보드 연결하기
5. 브레드 보드에 점퍼선, LED, 저항을 사용하여 회로 구성하기 
6. domino4 파일 실행 권한 주기
7. domino4 파일 실행하기 
---
## 동작 시연 영상

아래 사진을 클릭하면 동작이 시연되는 것을 확인해볼 수 있습니다.

[![시연과 설명 영상1](image/thumnail2.jpg)](https://www.youtube.com/watch?v=qqGw-CTZCQk)

--- 
## 하드웨어

![회로도1](count/image1/회로도1.jpg)

| LED 순서 | 핀 번호 |
|----------|---------|
|   첫 번째  | 2번 핀 (IO2) |
|   두 번째  | 17번 핀 (IO17) |
|   세 번째  | 10번 핀 (IO10) |
|   네 번째  | 11번 핀 (IO11) |

---

## 소프트웨어
```bash
#!/usr/bin/bash

pin1=2
pin2=17
pin3=10
pin4=11

while true; do
    pinctrl set $pin1 dh
    sleep 1
    pinctrl set $pin1 dl
    pinctrl set $pin2 dh
    sleep 1
    pinctrl set $pin2 dl
    pinctrl set $pin3 dh
    sleep 1
    pinctrl set $pin3 dl
    pinctrl set $pin4 dh
    sleep 1
    pinctrl set $pin4 dl
done
```


___
## 주의 & 참고 사항
- 좌표가 헷갈리는 것 주의
    - 화면상 오른쪽으로 갈수록 x좌표 값이 증가
    - 화면상 아래쪽으로 갈수록 y좌표 값이 증가 
- == 와 ===의 차이점
    
    `==`와 `===`는 JavaScript에서 비교 연산자로 사용되며, 그 차이는 **"타입 변환 여부"**입니다.
    
    1. **`==` (동등 연산자)**:
        - **타입 변환**을 허용합니다.
        - 비교 대상의 값이 서로 다른 타입이라도, 비교 전에 자동으로 타입 변환을 시도하여 비교합니다.
        - 예를 들어, 숫자와 문자열을 비교할 때, 문자열이 숫자로 변환되어 비교됩니다.
        
        ```jsx
        5 == "5"  // true (문자열 "5"가 숫자 5로 변환되어 비교됨)
        null == undefined  // true (null과 undefined는 동등함)
        
        ```
        
    2. **`===` (일치 연산자)**:
        - **타입 변환을 하지 않고, 값과 타입이 모두 동일해야** true를 반환합니다.
        - 비교 대상이 **동일한 타입**이어야 하고, **값도 동일**해야 true를 반환합니다.
        - 더 엄격한 비교 방식입니다.
        
        ```jsx
        5 === "5"  // false (타입이 다름)
        null === undefined  // false (타입이 다름)
        
        ```

- p5.js에서 index.html파일에 ml5를 사용하기 위해 추가해야 하는 코드입니다.   
        ```
        <script src="https://unpkg.com/ml5@1/dist/ml5.min.js"></script>
        ```

---

# 📌 임베디드통신시스템 과제1

## 📖 소개

[임베디드통신시스템]강의의 첫 과제로 Arduino와 p5.js를 이용하여 신호등을 제어하는 시스템을 만들어보았습니다. Arduino코드를 짤 때는 vs code에 platformIO를 설치하여 코드를 작성하였습니다.

## 과제 설명

![이미지 설명](image/assignment_description.png)
![이미지 설명2](image/assignment_description2.png)

## 동작 시연 영상

아래 사진을 클릭하면 동작이 시연되는 것을 확인해볼 수 있습니다.

[![시연과 설명 영상](image/thumnail.jpg)](https://www.youtube.com/watch?v=7Dofh5zMiac)

---

## vs code에 platformIO를 설치하는 방법
vs code에서 platformIO가 설치되어있지 않았을 경우를 위해 설명을 간단히 적어보았습니다.  
1. vs code의 좌측에 5번째 항목에 해당하는 확장(extension)을 클릭
2. platformIO를 검색
3. 설치
4. 좌측에 개미모양 아이콘이 생기면 클릭
5. new project를 클릭
6. 프로젝트 이름을 원하는 이름으로 설정
7. 사용할 보드 선택 (저는 Arduino Uno를 사용했습니다.)

### 라이브러리에서 프로젝트에 추가
add project하여 추가하고 싶은 프로젝트를 선택
- TaskScheduler by Anatoli Arkhipenko
- PinChangeInterruptHandler by Andreas Rohner  

---
## 하드웨어
### 회로도
직접 연결한 회로도와 틴커캐드로 보기 쉽게 정리한 회로도 사진입니다.
- 직접 연결한 회로도
![회로도1](image/circuit_me.jpg)

- 틴커캐드로 정리한 회로도 사진
![회로도2](image/tinkercad.png)

| 연결된 부품 | 핀 번호 | 상태 |
|-----------|---------|------|
| 빨간색 LED | D6 | 🔴
| 노란색 LED | D3 | 🟡
| 초록색 LED | D5 | 🟢
| 버튼1 | D7 | 1️⃣
| 버튼2 | D8 | 2️⃣
| 버튼3 | D9 | 3️⃣
| 가변저항 | A0 | 🔆
| 전원 | 5V | 🔌
| 접지 | GND |  ⏚ 
---

## 소프트웨어

- 자세한 코드는 코드에 포함되어 있는 주석 참고

### Arduino

1️⃣ 아두이노 부팅 시 setup() 실행  
2️⃣ 각 버튼에 대해 인터럽트 설정 (attachPCINT)  
3️⃣ loop()에서 runner.execute() 실행 (TaskScheduler가 모든 동작 관리)  
4️⃣ 버튼을 누르면 모드가 변경되고, setMode()에서 해당 모드의 Task를 실행  
5️⃣ 가변저항을 통해 LED 밝기 조절 가능  
6️⃣ p5.js에서 시리얼 통신으로 신호등 시간 조정 가능  

### p5.js

아두이노와의 시리얼 통신을 통해 신호등 시스템을 웹 UI로 제어할 수 있도록 설계하였습니다.
사용자는 연결 버튼을 눌러 아두이노와 연결하고, 슬라이더를 이용해 신호등의 점등 시간과 밝기를 조절할 수 있습니다.
실제 신호등 상태는 UI에서 실시간으로 반영되며, 설정한 값은 아두이노에 전송됩니다.  
1️⃣ 시리얼 포트 연결 관리   
2️⃣ 신호등 상태 표시 (drawColorCircle())  
3️⃣ 슬라이더 및 버튼을 이용한 값 조정  
4️⃣ 모드 및 밝기 UI 업데이트 (drawIndicators(), drawBrightnessGauge())  
5️⃣ 화면 UI 요소 초기화 (setup())  

___
## 주의 & 참고 사항
- PWM이 지원되는핀으로 LED핀 번호를 설정해야 alalogWrite()를 지원합니다. 
    - PWM이 지원되는 핀 번호 : 3, 5, 6, 9, 10, 11

- loop()함수에서 delay()를 쓰게 되면 시간 지연이 발생할 수 있습니다.
    - loop()함수에서는 가급적 스케줄러만 동작하도록 하는 것이 좋습니다. 

- 라이브러리를 프로젝트에 미리 추가하여야 실행 가능합니다. 

- attachPCINT(digitalPinToPCINT(BUTTON1), buttonPressed1, FALLING); 명령어에서 FALLING은 하강엣지일 때를 의미합니다. 즉, 버튼을 누를 때 작동합니다. 
    - FALLING대신 CHANGE를 사용하면 버튼을 누르면 눌렀을 때와 땠을 때 모두 작동합니다. 
    - FALLING대신 RISING을 사용하면 버튼을 누르고 손가락이 때질 때 작동합니다. 

- TaskScheduler 사용하는 이유
    - delay() 없이 주기적인 작업을 쉽게 만들 수 있습니다.
    - 비동기 작업 처리 → delay() 없이 여러 작업을 동시에 실행 가능
    - CPU 효율적 사용 → 필요할 때만 실행되므로, loop()가 깔끔해짐
    - 우선순위 제어 → 특정 태스크의 실행 주기를 쉽게 조절 가능
    - 확장성 → 여러 개의 기능을 쉽게 추가 가능

- pinChangeInterrupt 사용하는 이유
    - 특정 핀의 상태가 변경될 때마다 자동으로 인터럽트를 발생시켜 처리하는 기능입니다.
    - 빠른 반응 속도 → loop()에서 digitalRead()로 버튼 상태를 계속 확인하는 것보다 훨씬 빠름
    - CPU 절약 → loop()에서 지속적으로 폴링(polling)하지 않아도 됨
    - 정확한 입력 감지 → 버튼, 센서 등의 빠른 신호 변화를 놓치지 않음


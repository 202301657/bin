
# 📌 임베디드통신시스템 5주차 과제1

## 📖 소개

[임베디드통신시스템]강의의 5주차 첫 번째 과제로 라즈베리 파이와 GPIO를 이용하여 LED를 제어하는 시스템을 만들어보았습니다. 

## 과제 설명

![missionA](domino/image1/missionA.png)

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
직접 연결한 회로도 사진입니다. 
![GPIO](domino/image1/GPIO.jpg)
![회로도1](domino/image1/회로도1.jpg)

| LED 순서 | 핀 번호 |
|----------|---------|
|   첫 번째  | 2번 핀 (IO2) |
|   두 번째  | 17번 핀 (IO17) |
|   세 번째  | 10번 핀 (IO10) |
|   네 번째  | 11번 핀 (IO11) |

---

## 소프트웨어
### 명령어 정리
디렉토리, 파일 관련련
- ls : 현재 디렉토리에 있는 디렉토리와 파일 목록을 보여줌.
- mkdir domino : domino라는 디렉토리 만듦. 
- cd domino/ : domino 디렉토리로 이동 
- touch domino4 : domino4 파일을 만듦.  
- nano domino4 : domino4 파일 내용 편집 (다른 편집기를 사용해도 좋음.) 
    - 아래에 있는 bash코드 확인 
- cat domino4 : 터미널에서 파일 내용 확인 가능함. 
- ls -l : 읽기, 쓰기, 실행권한 여부를 보여줌. (여기서는 실행 권한이 있는지 확인하기 위해 쓰임.)
- source ~/.profile : 어느 디렉토리에 있든 찾는 파일을 실행시킬 수 있음.
- which domino4 : domino4 파일의 위치를 알려줌. 
- domino4 : domino4 코드 실행.

GPIO 관련 
- pinctrl -p get : 현재 모든 GPIO 핀의 상태를 출력
- pinctrl set 핀 번호 __ 
    - ex : pinctrl set 2 op    

    | 필드(__)	| 의미 |    
    |-------|--------|    
    | ip  | 입력(Input) 모드 |   
    | op  | 출력(Output) 모드 |
    | pu  | Pull-up |
    | pd  | Pull-down |
    | dh  | 출력 상태가 High (1) |
    | dl  | 출력 상태가 Low (0)  |
    | no  | 미설정(Not used) 상태  |


```bash
#!/usr/bin/bash

pin1=2 # 첫 번째 LED
pin2=17 # 두 번째 LED
pin3=10 # 세 번째 LED
pin4=11 # 네 번째 LED

# 각 핀을 출력 모드(op)로 설정
pinctrl set $pin1 op 
pinctrl set $pin2 op
pinctrl set $pin3 op
pinctrl set $pin4 op

while true; do
    pinctrl set $pin1 dh # 첫 번째 LED 켬
    sleep 1 # 1초 유지
    pinctrl set $pin1 dl # 첫 번째 LED 끔
    pinctrl set $pin2 dh # 두 번째 LED 켬
    sleep 1 # 1초 유지
    pinctrl set $pin2 dl # 두 번째 LED 끔
    pinctrl set $pin3 dh # 세 번째 LED 켬
    sleep 1 # 1초 유지
    pinctrl set $pin3 dl # 세 번째 LED 끔
    pinctrl set $pin4 dh # 네 번째 LED 켬
    sleep 1 # 1초 유지
    pinctrl set $pin4 dl # 네 번째 LED 끔
done
```
___
## 주의 & 참고 사항

- GPIO 핀에서 0번과 1번은 아두이노와 연결할 때 쓰이며 일반적인 GPIO 용도로는 사용되지 않습니다. 

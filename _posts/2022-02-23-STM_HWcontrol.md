---
layout: single
title: "[2. 하드웨어의 제어]"
categories: [STM32]
toc: true
author_profile: false
sidebar:
  nav: "docs"
---

# 1. SFR을 이용한 하드웨어 제어

| GPIO | SFR에 값을 기록하여 전기적 상태를 변경 <br> 핀의 전기적 상태의 확인 |
| TIMER | SFR 값이 하드웨어 적으로 계속 변화 <br>(시간정보 구하는데 사용) |
| ADC | 핀의 전압이 digital로 변환되어 SFR에 기록 |
| DAC | SFR에 값을 기록하면 전압값이 변경된다. |
| UART / SPI / I2C | 전송하려는 데이터를 SFR에 기록 |

<br><br><br>

# 2. 외부 하드웨어와의 연결

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F52a12ba0-225f-4c5e-ad3f-b6f0475a23e5%2FUntitled.png?table=block&id=96a91ad0-7d88-446a-9f4b-0cb525629762&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

STM 32의 경우, 각 핀에 다양한 외부 하드웨어가 연결되어 있다
- LED
- Function key
- FND (Flexible Numeric Display)
- Light Sensor

Port는 크게 Port A, Port B, Port C로 구분

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F126f1020-76d4-47d0-941a-d6d5b108dac3%2FUntitled.png?table=block&id=9f92505a-f3ba-4e44-b4ba-48f2fbbb217a&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)
각 핀의 전기적 상태를 변경하여 외부 하드웨어를 제어 및 사용할 수 있다.

## (1) GPIO (일반 입출력 포트)

### ① GPIO 사용을 위한 클록 설정

![Untitled](https://www.notion.so/signed/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F126f1020-76d4-47d0-941a-d6d5b108dac3%2FUntitled.png?table=block&id=9f92505a-f3ba-4e44-b4ba-48f2fbbb217a&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&name=Untitled.png&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F58725b71-07a6-4669-b986-f58d9ceed7db%2FUntitled.png?table=block&id=515e233e-bc1d-4edc-8532-35044150a3a9&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

Peripheral Clock enable register를 건들여서 Port의 설정을 사용할 수 있도록 만들어주자.

RCC_APB2ENR에서 클록 설정을 할 수 있다.

이때, RCC의 기본 설정 주소는 0x4002.1000이다.

여기에 APB2의 주소는 0x18이다!

그러므로 0x4002.1018에 여기에 사용하려는 Port에 따라 신호를 줄 비트의 위치가 바뀐다.

- Port A : RCC_APB2ENR[2] = 1
- Port B : RCC_APB2ENR[3] = 1
- Port C : RCC_APB2ENR[4] = 1


### ② 핀의 전기적 신호를 바꾸는 방법

| GPIOx_CRL | 0 ... 7번핀 방향설정에 사용하는 SFR (Configuration Low) |
| GPIOx_CRH | 8 ... 15번핀 방향설정에 사용하는 SFR (Configuration High) |
| GPIOx_IDR | 핀의 전기적 상태를 확인하는 SFR (Input Data Register) |
| GPIOx_ODR | 핀의 전기적 상태를 변경하는 SFR (Output Data Register) |

### ③ GPIO_CRL, GPIO_CRH

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6e729bc7-8bf0-4299-8427-0840d09073e5%2FUntitled.png?table=block&id=f2cd2cd3-4ab8-40f4-87d5-9e9bcdda03f9&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

1. 입출력 방향 설정

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F54b8e1ba-455f-4661-b736-4741f8873ac1%2FUntitled.png?table=block&id=2056b012-0fdd-4d73-9591-7df4eb7022eb&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

각 핀마다 할당된 CNF와 MODE 4비트를 변경하여 설정

입력 CNF : 01

- Mode 00 : input mode

출력 CNF : 00

- Mode 10 : 속도 2MHZ
- Mode 01 : 속도 10MHZ
- Mode 11 : 속도 50MHZ

2. 특수목적(PWM, 통신 등)으로 사용할 것인가에 대한 설정

3. 출력/입력 방식 설정(출력 속도, 출력 방식 / 입력 방식)

### ④ GPIO_IDR

외부 신호에 따라 변화하는 핀의 전기적 상태를 알 수 있다.

0x4001.0808의 각 비트의 변화를 보고 전기적 상태를 파악할 수 있다.

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcdf61806-9d33-493c-9fa1-26d744f6b3a3%2FUntitled.png?table=block&id=a35e9382-feb4-43be-aabc-c78ee90283bf&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

### ⑤ GPIO_ODR

핀의 전기적 상태를 바꿀수 있다

0x4001.080C의 각 비트를 변경하여 신호를 변경할 수 있다.

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2d990c68-0a60-4c43-a108-f08a74273716%2FUntitled.png?table=block&id=50c46c10-25cf-4e17-b2db-eeca1d5118b2&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

<br><br><br>

# 3. 인터럽트

프로세서가 프로그램을 순차적으로 수행하고 있을때, 외부 장치에서 특정 상황이 발생한 경우 프로세스가 예외적인 프로그램이 처리하게 하는 것.

## (1) 내부 인터럽트

### ① 하드웨어 고장(Hardware Interrupt)
- 컴퓨터 고장
- 데이터 전달 과정에서의 비트 오류
- 전원이 나간 경우

### ② 실행할 수 없는 명령어
- 기억장치에서 인출한 명령어의 비트 패턴이 정의되어 있지 않은 경우

### ③ 명령어 실행 오류
- 나누기 0을 하는 경우

### ④ 사용 권한 위배
- 사용자가 운영체제만 사용할 수 있는 자원에 액세스하는 경우

## (2) 외부 인터럽트

주변 IP의 SFR에 기록된 정보에 따라 특정 조건이 되면 Processor쪽으로 인터럽트 신호 전달. <br>
Processor는 ROM에 있는 인터럽트 서비스 함수의 주소 정보를 가지고 온다. <br>
이때 사용되는 인터럽트 서비스 함수, 즉 ISR은 예외 상황을 처리하기 위해 구현된 프로그램이다. <br>
이를 위해 SP와 PUSH와 POP이 사용된다. <br>

### ① 타이머 인터럽트

타이머가 일정한 시간 간격으로 중앙처리장치에게 인터럽트를 요청 <br>
내부 System timer SFR을 조정하여 주기적으로 인터럽트 신호를 주게 할 수 있다!

### ② 입출력 인터럽트

속도가 느린 입출력장치가 입출력 준비가 완료되었음을 알리기 위해 인터럽트를 요청
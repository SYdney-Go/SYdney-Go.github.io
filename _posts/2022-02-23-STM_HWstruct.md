---
layout: single
title: "1. 하드웨어의 구조"
categories: [STM32]
toc: true
author_profile: false
sidebar:
  nav: "docs"
---

# 1. STM32의 구조

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5ee8e6a2-e686-4958-be3a-7a2b2ba49438/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T005755Z&X-Amz-Expires=86400&X-Amz-Signature=8bc9a888353deda20a86855fe6ca2cff5432a411561243f499c2d8c88bc3c1cf&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


## (1) Cortex-m3 내부 MCU

STM32-entry에 사용되는 MCU <br>
단일 칩 내부에 프로세서, 메모리, 입출력 장치를 갖춘 장치

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c17a55df-c4bb-49b9-abc6-f5e858051a61/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T005832Z&X-Amz-Expires=86400&X-Amz-Signature=6515cea9d2216cef74b6bb0355b7c021959d9b865cd304cee7407aa707f51351&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

## (2) Processor

중앙 처리 장치 =  ALU + 레지스터

- 프로그램 카운터(PC) <br>
    &emsp;다음에 수행될 명령어의 주소를 보관하고 있는 레지스터
- 명령어 레지스터(IR)<br>
    &emsp;가장 최근에 인출된 명령어를 보관하고 있는 레지스터
- 누산기(AC)<br>
    &emsp;연산 결과를 임시적으로 보관하는 레지스터
- 기억장치 주소 레지스터(MAR)<br>
    &emsp; 읽기와 쓰기 연산을 수행할 주 기억장치의 주소 기억
- 기억장치 버퍼 레지스터(MBR)<br>
    &emsp;주기억장치의 데이터나 주기억장치에서 쓰거나 읽을 임시 데이터를 보관하는 레지스터
- 스텍 포인터(SP)<br>
    &emsp;스택영역의 번지를 지정해주는 레지스터
    

### ① Register (범용 레지스터)

프로세서가 바로 사용할 수 있는 데이터를 담고 있는 메모리

### ② SFR (특수 레지스터)

#### - 프로그램 제어 및 연산용 레지스터

| 산술 및 논리 연산 |  ACC, B |
| 외부 데이터 메모리의 주소 관리 | DPTR(DPL, DPH)     |
| 프로그램 상태 관리 | PSW     |
| 스택의 주소 관리 | SP |

★ MCU 레지스터 13, 14, 15번 ★
- 13번은 스택 포인터로 사용된다
- 14번은 함수 호출이 끝난 뒤 복귀 위치의 주소를 가지고 있다.
- 15번은 PC (현재 사용하려는 명령어의 주소 정보로 사용된다.)

#### - 마이크로프로세서의 주변 기기 제어용 레지스터

MCU에도 들어있지만, 각 IP에도 들어있다!<br>
모든 SFR의 내부에는 memory mapping 되어있어서 특정 주소로 하드웨어를 제어할 수 있다.<br>
각 비트가 하드웨어적인 의미를 가지고 있기 때문이다.

| 포트 제어 |  P0～P3 |
| 외부 데이터 메모리의 주소 관리 | DPTR(DPL, DPH)     |
| 프로그램 상태 관리 | PSW     |
| 인터럽트 제어 | IE, IP  |
| 외부 인터럽트 제어 | TCON |
| 타이머 인터럽트 제어 | TMOD, TCON, TH1, TL1, TH0, TL0  |
| 직렬 송수신 제어 | SBUF, SCON, PCON |


## (3) ALU

**산술연산과 논리연산**을 하는 연산장치

## (4) Bus

코어와 레지스터와 메모리를 연결해주는 회로를 말한다.

- 데이터를 처리하는 중앙 처리 장치
- 프로그램을 담고 있는 메모리
- 바깥 세계와 통신하는 주변기기
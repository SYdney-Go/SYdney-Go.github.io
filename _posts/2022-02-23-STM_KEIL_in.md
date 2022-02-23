---
layout: single
title: "3. KEIL 개발 환경 사용"
categories: [STM32]
toc: true
author_profile: false
sidebar:
  nav: "docs"
---

# 1. KEIL IDE

![Untitled](https://www.notion.so/signed/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F95e376c3-ad4d-45d4-9057-b3349c5fd676%2FUntitled.png?table=block&id=7a0f7224-4c26-4e23-9b14-c16ec7723ca4&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&name=Untitled.png&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

가장 많이 사용되는 임베디드 IDE 중 하나로, 가상의 환경을 제공하거나 실제 칩을 연결해서 환경을 설정할 수 있다.

특히 강력한 디버깅 기능을 제공한다.

우리가 사용하는 ARM Cortex-M3 MCU를 장착한 STM32의 가상환경을 제공한다.

<br><br><br>

# 2. KEIL 설치

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc2b2e73c-cae6-4caa-9cb3-57e56ea2c524%2FUntitled.png?table=block&id=af80af64-8e7e-416b-b193-6614546f273a&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

## (1) Software package 설치

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa67326d9-6efc-4957-8993-9e9733c1306d%2FUntitled.png?table=block&id=a8adcdba-a15a-48e4-bd5e-0d4dd010d06e&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fabc8671b-d517-4b6a-8ee9-eeea9b52cad3%2FUntitled.png?table=block&id=899c5c43-c444-46e0-bf8d-21fbe5fdba12&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

<br><br><br>

# 3. 프로젝트 생성 방법

## (1) 새 프로젝트 생성

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F52823e1d-a806-4be7-90b0-8f4c8107ef96%2FUntitled.png?table=block&id=3a1b8ba0-93c6-41ab-8f9b-9a33db50d55a&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc596affd-27b8-4f70-a7d6-b4587128f563%2FUntitled.png?table=block&id=7f2a6578-e527-43f6-8aac-f2d076b23deb&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

## (2) 내부 가상환경을 사용하는 경우

### ① 사용할 가상환경의 MCU 선택하기

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc19b1e3a-7e9f-4f14-a071-d8c765fe3391%2FUntitled.png?table=block&id=13df3b6d-ba12-4ac8-b76a-fff64edaa058&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

### ② 빌드 설정의 진행

#### - 표준 라이브러리 함수 사용을 위한 설정과 사용할 메모리 크기 값을 설정

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fffa6b90d-5865-41cf-938d-60d90178f4c3%2FUntitled.png?table=block&id=8a17c629-fc23-4cec-a8cc-5c13f923edd4&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

#### - Hex파일과 bin 파일 생성 설정

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3022900d-5103-4c05-bb04-0c85ab0ce053%2FUntitled.png?table=block&id=bd972aee-7a10-493f-8cf3-56b4cc373a4d&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F95754381-dda5-4c2a-af9f-586a788b7bb9%2FUntitled.png?table=block&id=b5bc1529-15c0-4881-8f13-d9d81316a023&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

C:\Keil_v5\ARM\ARMCC\bin\fromelf.exe --bin "#L" -o "$P\output.bin”

#### - 링크와 디버거 설정

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc38554b7-68be-4732-8a05-9fc60db44798%2FUntitled.png?table=block&id=e7e0b8d8-7273-4ce9-a929-9c47a26db2ad&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F74c99ded-3510-461a-a182-12934bf761e0%2FUntitled.png?table=block&id=e643cc62-5014-49db-adeb-a29a2d7aa5d8&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

## (3) 외부 CPU를 사용하는 경우

### ① 사용하려는 CPU를 선택

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F481e61e0-d800-4c2a-b609-41a5b5206837%2FUntitled.png?table=block&id=8da3e47e-84a9-4f7e-81a4-8a88a11e9034&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe4e2c91e-1c30-4a1b-973d-3282cfb1b8af%2FUntitled.png?table=block&id=a26134f8-c8ee-49ae-bb31-8adcddc81e5a&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F48ca46a6-fe2f-4193-a558-c52fdc67691e%2FUntitled.png?table=block&id=f680db8b-55f8-451c-a36a-c9bce57f6cb1&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F86b3a64c-96be-4b92-bdf3-18a4ccb78c87%2FUntitled.png?table=block&id=617379ad-619b-4985-8b45-43847086d643&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

### ② 파일 생성 후 프로젝트에 추가

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1f5f1209-4022-4829-9ddf-409bf35313b1%2FUntitled.png?table=block&id=30101377-53ee-4928-a0c2-4bbee3e23b1d&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7eb27a70-a6a6-48bf-910f-94aed83f74b1%2FUntitled.png?table=block&id=40a680e8-5ca3-4187-8509-11390e03c7b5&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

### ③ 빌드 설정의 진행

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F05d1ccfb-8762-4fd7-8b62-dbdd989379fe%2FUntitled.png?table=block&id=d0b4191f-633f-4d51-96b6-14cb8a1e0063&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

#### - 메모리 영역 확인

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6175f0d9-edc6-4a82-a2aa-b3bd8277fc88%2FUntitled.png?table=block&id=765fd3f1-ba44-4119-af4d-8a02e8a765bd&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

#### - MAP파일과 HEX 파일 생성 설정

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffe8b4319-b9f9-479d-aa6b-86a913b8b261%2FUntitled.png?table=block&id=7211abe9-179d-4721-a59f-fd49c9238508&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F957d305a-39a1-45e9-a331-1c0f06dfb13c%2FUntitled.png?table=block&id=85294674-0b4b-46d5-9c48-b5ffd65a96b2&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

#### - bin 파일 생성 : C:\Keil_v5\ARM\ARMCC\bin\fromelf.exe --bin "#L" -o "$P\output.bin”

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F05b7915c-ad3c-40f6-80ec-0d9b639670ee%2FUntitled.png?table=block&id=04fe27ae-e0db-435f-b7bf-86bc6e82db19&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

#### - 사용할 디버거 설정

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Facd7208b-2234-45a9-8ca4-bbfd43712719%2FUntitled.png?table=block&id=56169854-7931-427a-b02d-af87f5af2e0c&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

<br><br><br>

# 4. 프로젝트 빌드

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F37c8b5e7-295a-4fd7-ba28-f97c0c14938c%2FUntitled.png?table=block&id=5ec32c22-da19-4890-bf7a-02ebb0ad48a4&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

<br><br><br>

# 5. ST-Link

ST-Link처럼 마이크로컨트롤러와 통신하는 도구들을 JTAG라고 한다!

빌드 결과물을 외부 CPU의 내부ROM에 다운로드 해보자!

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fdd24dcf0-3936-49ae-a236-9a3722968f2a%2FUntitled.png?table=block&id=eee5bd02-093e-4741-a895-970c0d84e1d4&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

- ST-Link : 다운로드, 디버깅 기능

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcbbbee15-0eda-4ead-9316-a853dbff487f%2FUntitled.png?table=block&id=b6b53944-a8d2-448a-b8f5-8c6f37b1251f&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

- USB 케이블 : PC에서 전원 공급, 시리얼 통신 기능

<br><br><br>

# 6. Build

개발자가 소스코드를 작성하면 컴파일러가 이를 프로세서가 이해할 수 있는 명령어로 변환해준다.

이 파일을 오브젝트 파일로 변환을 한다.

오브젝트 파일은 링커와 연결되어 최종적으로  axf 파일이 생성되게 된다. 또 추가적으로 hex와 bin 파일도 형성이 된다.

- hex : 아스키 형태의 텍스트로 구성되어있으며, 시작 코드와 바이트 수, 주소 등의 정보를 가진다.
- bin : 순수한 raw data를 의미한다. → ROM Binary

이렇게 빌드된 이진 결과물은 JTAG를 통해서 ROM에 구워지게 되고, 실행 과정을 디버깅할 수 있다.

<br><br><br>

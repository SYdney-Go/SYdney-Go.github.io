---
layout: single
title: "4. KEIL 코드 최적화"
categories: [STM32]
toc: true
author_profile: false
sidebar:
  nav: "docs"
---

# 1. Volatile 최적화

### volatile 변수

항상 해당 변수를 최적화에서 제외해서 레지스터에 로드된 값을 사용하지않고, 매번 메모리를 참조한다.

반복하여 사용할건데 굳이 그래야하는 이유가 있다!

SFR의 경우, 최적화해버리면 외부 요인에 의해 변경된 하드웨어의 변화를 감지할 수 없기 때문이다..

따라서 SFR접근을 하는 경우에는 되도록 volatile 키워드를 사용해주자

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F89f8e340-bbe2-4f32-a406-0e8912134b4f%2FUntitled.png?table=block&id=59c0cebe-6224-43bc-80be-cc46a37217de&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)

### 최적화

그 외의 경우, 특히 순수 알고리즘과 관련된 문제에서는 최적화를 하면 메모리를 줄이거나 속도를 높일수 있다.

Level3 : 최대 최적화한 경우

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2a3765e7-5295-4e7a-9cfb-f03073fd30c2%2FUntitled.png?table=block&id=82234847-8ca6-4e74-9335-83b28b7148c2&spaceId=7a6b4b37-d969-4d36-a069-a8add2591900&width=2000&userId=ff8f58fa-3d3e-43a0-99fa-e0ff405dfa57&cache=v2)
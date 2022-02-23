---
layout: single
title: "KEIL 코드 최적화"
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

![Untitled](Part%202%20KEI%20c1bc0/Untitled%2037.png)

### 최적화

그 외의 경우, 특히 순수 알고리즘과 관련된 문제에서는 최적화를 하면 메모리를 줄이거나 속도를 높일수 있다.

Level3 : 최대 최적화한 경우

![Untitled](Part%202%20KEI%20c1bc0/Untitled%2038.png)
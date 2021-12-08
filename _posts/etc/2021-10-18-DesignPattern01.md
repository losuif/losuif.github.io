---
title: "[디자인패턴] 디자인 패턴 (Design Patern)"
author: Jinsol
categories: DesignPattern
tags: Spring Java DesignPattern
date: '2021-10-18'
# image: /assets/img/.png
---

<br>

## <span style="color:#1E5128">디자인 패턴</span>

<hr>
<br>

- 자주 사용하는 설계 패턴을 정형화 해서 이를 유형별로 가장 최적의 방법으로 개발 할 수 있도록 정해둔 설계

- 알고리즘과 유사하지만, 명확하게 정답이 있는 형태 X, 프로젝트의 상황에 맞추어 적용 가능

- 디자인 패턴의 장점

    - 개발자간의 원활한 소통

    - 소프트웨어 구조 파악 용이

    - 재사용을 통한 개발 시간 단축

    - 설계 변경 요청에 대한 유연한 대처

    - 요구사항 변경에 따른 소스코드 변경 최소화

- 디자인 패턴의 단점

    - 객체지향 설계/구현 위주로 사용됨

    - 초기 투자 비용 부담 (초기에 여러 구조를 설계하고 코딩해야 함)

<br>

#### <span style="color:#1E5128">생성 패턴</span>

<hr>

- 객체를 생성하는 것과 관련된 패턴

- 객체의 생성과 변경이 전체 시스템에 미치는 영향을 최소화 하고, 코드의 유연성을 높여줌

-   - Factory Method

    - Singleton

    - Prototype

    - Builder

    - Abstract Factory

    - Chaining

<br>

#### <span style="color:#1E5128">구조 패턴</span>

<hr>

- 프로그램 내 자료구조나 인터페이스 구조 등 프로그램 구조를 설계하는데 활용 될 수 있는 패턴

- 클래스, 객체들의 구성을 통해 더 큰 구조를 만들 수 있게 해줌

- 큰 규모의 시스템에서는 많은 클래스들이 서로 의존성을 가짐 > 복잡한 구조를 개발 하기 쉽게 만들어 주고, 유지 보수 하기 쉽게 만들어줌

-   - Adapter

    - Composite

    - Bridge

    - Decorator

    - Facade

    - Flyweight

    - Proxy

<br>

#### <span style="color:#1E5128">행위 패턴</span>

<hr>

- 반복적으로 사용되는 객체들의 상호작용을 패턴화한 것

- 클래스나 객체들이 상호작용하는 방법과 책임을 분산하는 방법 제공

- 행위 관련 패턴을 사용하여 독립적으로 일을 처리하고자 할 때 사용

-   - Template Method

    - Interpreter

    - Iterator

    - Observer

    - Strategy

    - Visitor

    - Chain of reponsibility

    - Command

    - Mediator

    - State

    - Memento
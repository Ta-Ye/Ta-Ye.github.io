---
layout: post
title: 관계형 데이터 모델링 1
subtitle: 개념적 데이터 모델링
tags: [RDB]
comments: true
---


## 업무 파악

---

### 기획

데이터 모델링이란 데이터베이스를 통해 현실의 문제를 해결하는 것이다. 따라서 컴퓨터를 이해하는 것 만으로는 부족하고 업무 이해를 깊게 해야 가능하다. 그러기 위해서는 실무자들과  정확한 소통이 필요하다. 기획자와 구현자는 프로그램에 대한 UI(User Interface)를 함께 그려보며 서로 원하는 부분을 공유하고 동기화 하는 것도 좋다.

간단하게 UI를 구성해볼 수 있는 사이트

[OvenApp.io](https://ovenapp.io/)

## 개념적 데이터 모델링

---

### 소개

개념적 모델링이란, 파악한 업무에서 개념을 뽑아내는 것을 말한다. 개념적 모델링을 할 경우 다음과 같은 효과를 얻을 수 있다. 먼저, 현실에서 개념을 추출하는 일종의 필터를 준다. 문제에서 구현해야 하는 것들을 구조화 할 수 있는 능력을 갖는 것이다.

### 관계형 데이터베이스 다운 개념의 구조

![rdb1.png](/assets/img/RDB1.png)
Entity Relationship Diagram

관계형 데이터베이스는 개체 관계 구조 (ERD : Entity Relationship Diagram)에서 시작된다.  ERD는 정보, 그룹, 관계라는 3가지 구성 요소로 이루어 진다.

- 정보 (Entity) → table
- 그룹 (attribute) → column
- 관계 (Relation) → PK,FK

가령, 글을 올리고 댓글을 다는 사이트를 만든다고 가정하고 ERD를 만든다면 여러가지 형태로 나타낼 수 있다.

![rdb2.png](/assets/img/RDB2.png)

![rdb1.png](/assets/img/RDB3.png)

다른 형태도 있을 수 있지만 위 같은 두 가지 형태로도 표현할 수 있다. 하지만 RDB에서는 후자를 택해야 한다. 왜냐면 RDB는 내포관계를 허용하지 않기 때문이다.

![rdb1.png](/assets/img/RDB4.png)

내포하는 관계를 표로 표현할 경우 간단하게 표현할 수 없어 데이터 관리에 어려움이 있다.

![rdb1.png](/assets/img/RDB5.png)

하나하나 나눠서 표로 표현할 경우 중복이 발생하기 때문에 시스템 효율에 좋지 않다.

![rdb1.png](/assets/img/RDB6.png)

entity마다 표를 만들게 된다면 그룹화를 할 수 있고 원하는 정보에 해당하는 표만 봄으로서 컴퓨터의 자원을 아낄 수 있다는 장점이 있다.

출처

[관계형 데이터 모델링 - 4.2. 관계형 데이터베이스 다운 개념의 구조](https://www.youtube.com/watch?v=hbZ96tnbN4M&list=PLuHgQVnccGMDF6rHsY9qMuJMd295Yk4sa&index=6)

### ERD의 구성요소

개념적 모델링에서 정보들은 Entity, 정보의 속성은 Attribute, 연관성을 표현한 것을 Relation 이다.

후에 Entity는 표가 되고 Attribute는 표의 column이 되고 Realtion은 논리적 모델링에서 나오게 되는 FK가 된다.

- Entity

    database 와 UI는 원인과 결과의 관계를 가진다. 그렇기 때문에 순차적으로 점검해야 좋은 모델이 나올 수 있다. 따라서 기획자와 구현자가 다르다면 데이터 모델링 정도까지는 같이 해야 한다.

    ERD 에서는 기획서에서 Entity를 찾는 것을 먼저 해야 한다. 쓰기 화면에서 Entity를 찾기 쉽다.

- Attribute

    각각의 Entity가 가지는 속성으로 Entity가 시스템 적으로 필요로 하는 기능이 Attribute라 할 수 있다.

    식별자 (Identifier)

    Attribute 중에서 모든 행을 구분할 수 있는 것

    - 대체키 (alternate key) : 식별자로 사용할 수 있는 모든 속성
    - 기본키 (primary key) : 현재 식별자로 사용하는 속성
    - 후보키 (candidate key) : 기본키가 아닌 대체키
    - 중복키 (composite key) : 다수의 속성으로 대체키가 될 수 있는 것

    적당한 식별자가 없는 경우 인공적으로 식별자를 만들 수 있다. 일종의 일련번호 등

- Relationship

    Entity 간의 관계를 말한다.

    예를 들어, 글과 저자는 작성이라는 관계가 있다.

    예를 들어, 글과 댓글은 소속이라는 관계가 있다.

    - Cardinality
    - 1대1 관계

        ![rdb1.png](/assets/img/RDB7.png)

        예를 들어, 반과 담임에서 한 개의 반은 한 명의 담임만 있을 수 있고 한 명의 담임은 한 개의 반만 맡을 수 있다.  

    - 1대N 관계

        ![rdb1.png](/assets/img/RDB8.png)

        예를 들어, 반과 학생에서 한 개의 반은 여러 명의 학생을 가질 수 있고 한 명의 학생은 한 개의 반만 가질 수 있다.

    - N대N 관계

        ![rdb1.png](/assets/img/RDB9.png)

        예를 들어, 공유 문서에서 한 개의 공유 문서는 여러 명의 작성자를 가질 수 있고 한 명의 작성자는 여러 개의 문서를 작성할 수 있다.

    - Optionality

    ![rdb1.png](/assets/img/RDB10.png)

    - Mandatory

        예를 들어, 댓글은 작성자를 반드시 필요로 한다.

    - Optional

        예를 들어, 회원은 댓글을 달 수도 안 달 수도 있다.

Entity Relational Diagram Helper

[erd.yah.ac](http://erd.yah.ac/)
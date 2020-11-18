---
layout: post
title: 관계형 데이터 모델링 2
subtitle: 논리적 데이터 모델링
tags: [RDB]
comments: true
---


## 논리적 데이터 모델링

---

### Table 과 Column

Entity를 제목으로 하는 표(table)를 제작한다.

Table에 해당하는 Entity의 Attribute를 Column으로 하여  표를 구성한다.

### PK(Primary Key)와 FK(Foreign Key)

- PK (Primary Key)

    해당 Table에서 가장 기본적인 값을 가진다. 따라서 다른 항목과 절대로 중복되어 나타날 수 없는 단일 값(unique)을 가진다. 또한, 그렇기 때문에 null 값을 가질 수 없다.

- FK (Foreign Key)

    두 Table을 서로 연결하는데 사용되는 키이다. Foreign Key가 포함된 Table을 자식 Table 이라고 하고 Foreign Key 값을 제공하는Table을 부모 Table이라 한다.

예를 들어, 회원과 휴면 회원이라는 Entity가 있을 경우에는 휴면 회원의 아이디라는 Attribute는 회원의 아이디라는 Attribute에 포함된다. 따라서 회원과 휴면 회원은 아이디라는 Attribute에 대한 부모 자식 관계를 가진다.

Cardinality와 Optionality를 고려하여 지정한다. 

N대N 관계와 Mapping Table

연관 관계를 가진 Table 끼리는 FK가 반드시 존재하지만 N대N 관계에서는 그것을 정의하기가 까다롭다. 다중의 요소를 가질 수 있기 때문에 정렬하거나 원하는 값을 가져오는 것이 쉽지 않다.

Mapping Table은 Table간의 FK를 지정하기 어려울 때 사용한다. 다중의 요소를 가지는 관계를 1대1 관계로 바꿔서 Table을 연결 시켜준다.

예를 들어, 공유 문서의 경우 작성자가 다수이거나 글이 다수 일수도 있기 때문에 FK를 지정하기 어렵다. 이때는 Write라는 Mapping Table을 활용해 작성자 아이디와 글 번호를 맵핑할 수 있다.

### 참고

논리적 모델링을 할 수 있게 도와주는 eclipse tool

[ermaster.sourceforge.net](http://ermaster.sourceforge.net)
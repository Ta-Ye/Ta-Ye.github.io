---
layout: post
title: 관계형 데이터 모델링 3
subtitle: 정규화
tags: [RDB]
comments: true
---


## 정규화 (Normalization)

---

### 소개

정제되지 않은 표를 관계형 데이터베이스에 어울리는 표로 만들어 주는 방법이다.

![rdb1.png](/assets/img/RDB11.png)


단계별 정규화

### 제 1 정규화

Atomic column : 각 row는 column당 하나의 값만 가져야 한다.

제 1 정규화 전

![rdb1.png](/assets/img/RDB12.png)

Column tag의 행에 다수의 값이 존재할 수 있기 때문에 해당 부분에 대해 정규화를 해야한다.

제 1 정규화 오류 1.

![rdb1.png](/assets/img/RDB13.png)

tag를 한 개씩 쓰기 위해서 행을 나눴다. 하지만 tag를 제외하고 중복되는 행이 너무 많이 생기기 때문에 불필요한 데이터 낭비이다.  

제 1 정규화 오류 2.

![rdb1.png](/assets/img/RDB14.png)

여러 개의 tag Column을 만들어서 사용할 경우 tag의 개수가 늘어날 때마다 Column을 늘려야 하기 때문에 오류다. 

젹절한 제 1 정규화

![rdb1.png](/assets/img/RDB15.png)

topic Table의 PK인 title과 tag로 이루어진 mapping table을 새롭게 만들었다. 이럴 경우 불필요한 중복을 막을 수 있다.

### 제 2 정규화

No partial dependencies : 부분 종속성이 없어야 된다.

기본키 중에 중복키인 것이 있다면 제 2 정규화를 해야 한다.

제 2 정규화 전

![rdb1.png](/assets/img/RDB16.png)

type과 price의 차이로 인해 불필요한 중복이 발생했다.

적절한 제 2 정규화

!![rdb1.png](/assets/img/RDB17.png)

type과 price를 Column으로 가지는 mapping table을 만들어 불필요한 중복을 없앴다.

### 제 3 정규화

No transitive dependencies :  이행적 종속성이 없어야 한다.

제 3 정규화 전

!![rdb1.png](/assets/img/RDB17.png)

author_id, author_name와 author_profile은 항상 세트로 묶여있다. 이것을 이행적 종속성이라 한다. 

제 3 정규화 후

![rdb1.png](/assets/img/RDB18.png)

author라는 Table을 생성하여 불필요한 중복을 막는다.
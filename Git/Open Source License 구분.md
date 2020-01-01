# Open Source License 구분

*Assembled by GimunLee (2019-11-21)*

<br>

## 의무사항이 적고 사용하기 쉬운 오픈소스 라이선스

### 1. BSD

- 소스코드를 공개하지 않아도 되는 대표적인 라이선스입니다.
- 저작권 명시 (고지문)
- 적용 사례 : Nginx(The BSD 2-Clause License)

### 2. MIT

- MIT에서 해당 대학의 SW 공학도들을 돕기 위해 개발한 라이선스입니다.
- 라이선스 및 저작권 명시 (고지문)
- 적용 사례 : 부트스트랩, Angular.js, Backbone.js, JQuery

### 3. Apache

- 아파치 재단의 모든 SW에 적용되는 라이선스입니다.

- BSD 의무사항 + ***특허권 보장 (GPL 2.0으로 배포되는 코드와는 결합 불가능)**

  \*Apache 2.0의 특허 보복 조항을 GPL 2.0에서는 보장하지 않아 라이선스가 충돌합니다. (양립 불가능)

- 적용 사례 : 안드로이드 (v2.0), 하둡 (v2.0)

<br>

## 주의해야 할 라이선스

### 1. LGPL

- 수정한 소스코드를 LGPL로 공개해야합니다. (`Static Linking` 으로 사용하면 전체 코드 공개 의무 발생)
- LGPL 2.1 + Apache 2.0 = 결합 방식에 따라 배포 불가능할 수 있습니다.
- 라이선스 및 저작권 명시
- 적용 사례 : 모질라 파이어폭스 (v2.1)

### 2. GPL

- GPL을 사용한 프로젝트를 배포한 경우, 그 프로젝트의 전체 소스코드를 공개해야 합니다.
- 라이선스 및 저작권 명시
- 적용 사례 : 리눅스 커널 (v2.0)

### 3. AGPL

- AGPL 소스코드를 이용한 소프트웨어 전체를 AGPL로 공개해야합니다. **(웹 서비스 포함)**
- 라이선스 및 저작권 명시
- 적용 사례 : 몽고 DB (v3.0)
  - Database Server and Tools : AGPL 3.0
  - Drivers : Apache 2.0

<br>

## Reference & Addtional Resources

- [오픈소스를 사용하고 준비하는 개발자를 위한 가이드](https://github.com/GimunLee/tech-refrigerator/blob/master/Git/resources/%EC%98%A4%ED%94%88%EC%86%8C%EC%8A%A4%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%98%EA%B3%A0%20%EC%A4%80%EB%B9%84%ED%95%98%EB%8A%94%20%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%A5%BC%20%EC%9C%84%ED%95%9C%20%EA%B0%80%EC%9D%B4%EB%93%9C.pdf)
- https://www.slideshare.net/ifkakao/ss-113145564?from_action=save 



Git commit Test
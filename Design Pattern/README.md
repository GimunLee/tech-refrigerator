# 🍐 Design Pattern

*Assembled by Anna (2019-11-27)*

<br/>

## Goal

- Design Pattern의 목적을 알 수 있다.
- Design Pattern의 종류를 파악할 수 있다.

<br/>

## Why Design Pattern? 

기초 설계가 제대로 되지 않은 `클래스 구조의 개발`을 하다보면 제대로 된 객체지향적인 개발을 하지 못하게 됩니다. `Design Pattern`은 이러한 상황을 미연에 방지하고자 객체지향적인 클래스 설계 기법을 모아놓은 것입니다.

<br/>

## Design Pattern의 종류

GoF (Gang of Four) 라고 불리는 4명의 개발자가 23가지의 디자인 패턴을 구체화하고 용도에 따라 3가지의 영역(생성, 구조, 행위)로 나누었습니다.

### GoF 디자인 패턴

* ##### 생성(Creational) 패턴

  > 객체 생성에 관련하여, 특정 객체가 생성되고 변경되어도 프로그램 구조에 영향을 주지 않도록 유연성을 제공합니다.
  
  * 빌더 (Builder)
  * 팩토리 (Factory)
    * [팩토리 메소드 (Factory Method)](https://github.com/GimunLee/tech-refrigerator/blob/master/Design%20Pattern/Factory%20Pattern%20(1)%20-%20Factory%20Method%20Pattern.md#-factory-pattern-1---factory-method-pattern)
    * 추상 팩토리 (Abstract Factory)
  * 프로토타입 (Proto)
  * [싱글톤 (Singleton)](https://github.com/GimunLee/tech-refrigerator/blob/master/Design%20Pattern/Singleton%20Pattern.md#%EF%B8%8F-singleton-pattern)
    

* ##### 구조(Structural) 패턴

  > 클래스나 객체를 조합하여 더 큰 구조, 새로운 구조를 제공하는 패턴

  * 어댑터 (Adaptor)
  * 브리지 (Bridge)
  * 컴퍼지트 (Composite)
  * 데코레이터 (Decorator)
  * 퍼사드 (Facade)
  * 플라이웨이트 (Flyweight)
  * 프록시 (Proxy)
    

<br/>

* ##### 행위(Behavior) 패턴

  > 알고리즘이나 책임 분배에 관련된 패턴으로 객체 사이의 역할을 분담하며, 결합도를 최소화 하는 것에 중점을 둡니다.

  * [스트래티지 (Strategy)](https://github.com/GimunLee/tech-refrigerator/blob/master/Design%20Pattern/Strategy%20Pattern.md#-strategy-pattern)
  * [템플릿 메서드 (Template Method)](https://github.com/GimunLee/tech-refrigerator/blob/master/Design%20Pattern/Template%20Method%20Pattern.md#-template-method-pattern)
  * 이터레이터 (Iterator)
  * 커맨드 (Command)
  * 옵저버 (Observer)
  * 스테이트 (State)
  * 책임 연쇄, 인터프리터, 미디에이터, 메멘토, 비지터

<br/>

## Reference & Additional Resources

- <https://gmlwjd9405.github.io/2018/07/06/design-pattern.html>



 


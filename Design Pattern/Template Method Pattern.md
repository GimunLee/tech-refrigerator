# 🍐📋 Template Method Pattern

*Assembled by GimunLee (2019-12-05)*

<br/>

## Goal

- Template Method Pattern의 개념을 알 수 있다.
- Template Method Pattern의 사용 이점에 대해 설명할 수 있다.
- Template Method Pattern을 사용할 수 있다.
- 헐리우드 원칙과 Template Method Pattern의 관계에 대해 설명할 수 있다.

<br/>

## What is Template Method Pattern?

`Template Method Pattern` 에서는 메소드에서 알고리즘의 골격을 정의합니다. 알고리즘의 여러 단계 중 일부는 서브클래스에서 구현할 수 있습니다. 템플릿 메소드를 이용하면 알고리즘의 구조는 그대로 유지하면서 서브클래스에서 특정 단계를 재정의할 수 있습니다.

이번 장에서는 주어진 상황을 통해 Template Method Pattern의 사용 이점과 구현 방법에 대해 알아보도록 하겠습니다.

<br/>

## 스타버즈 커피 바리스타 훈련용 메뉴얼

스타버즈 **커피** 만드는 법

1. 물을 끓인다.
2. 끓는 물에 커피를 우려낸다.
3. 커피를 컵에 따른다.
4. 설탕과 우유를 추가한다.

스타버즈 **홍차** 만드는 법

1. 물을 끓인다.
2. 끓는 물에 차를 우려낸다.
3. 차를 컵에 따른다.
4. 레몬을 추가한다.

위와 같은 메뉴얼을 코딩으로 구현한다면 여러분은 어떻게 구현하실건가요?

<br/>

## 일반적인 커피 및 홍차 클래스 만들기 (JAVA)

#### Coffee Class

```java
public class Coffee {
   	void prepareRecipe(){
        boilWater(); // 물을 끓인다.
        brewCoffeeGrinds(); // 끓는 물에 커피를 우려낸다.
        pourInCup(); // 커피를 컵에 따른다.
        addSugarAndMilk(); // 설탕과 우유를 추가한다.
    }
    
    public void boilWater(){
        System.out.println("물 끓이는 중");
    }
    
    public void brewCoffeeGrinds(){
        System.out.println("필터를 통해서 커피를 우려내는 중");
    }
    
    public void pourInCup(){
        System.out.println("컵에 따르는 중");
    }
    
    public void addSugarAndMilk(){
        System.out.println("설탕과 우유를 추가하는 중");
    }
}
```

#### Tea Class

```java
public class Tea {
   	void prepareRecipe(){
        boilWater(); // 물을 끓인다.
        steepTeaBag(); // 끓는 물에 차를 우려낸다.
        pourInCup(); // 차를 컵에 따른다.
        addLemon(); // 레몬을 추가한다.
    }
    
    public void boilWater(){
        System.out.println("물 끓이는 중");
    }
    
    public void steepTeaBag(){
        System.out.println("차를 우려내는 중");
    }
    
    public void pourInCup(){
        System.out.println("컵에 따르는 중");
    }
    
    public void addLemon(){
        System.out.println("레몬을 추가하는 중");
    }
}
```

코드가 중복되어 있으면 디자인을 고쳐야 하지 않을까 생각해 보는 것이 좋습니다. Coffee하고 Tea 클래스가 거의 똑같으니까 공통적인 부분을 추상화시켜서 베이스 클래스를 만드는 것이 좋지 않을까요?

<br/>

## 일반적인 커피 및 홍차 추상화

<img src="./resources/template-method-pattern-001.png">

여러분도 위와 같이 생각하셨나요? **이 밖에 Coffee와 Tea 사이에 공통점이 더 없는지 생각해 봅시다.**

<br/>

## Template Method Pattern 사용하기

커피와 홍차 사이에 또다른 공통점은 만드는 법의 **알고리즘** 이 똑같다는 것 입니다. 다시 한번 스타버즈의 메뉴얼을 살펴보면,

1. 물을 끓인다.
2. 뜨거운 물을 이용하여 `커피 또는 홍차` 를 우려낸다.
3. 만들어진 음료를 컵에 따른다.
4. 각 음료에 맞는 첨가물을 추가한다.

이렇게 보니, 이미 추상화한 1번, 3번 이외에도 나머지 2번, 4번 또한 추상화가 가능할 것 같습니다. 먼저, 커피와 홍차에서 사용해도 이상하지 않도록 수퍼클래스의 메소드 이름을 바꿔보겠습니다.

#### CaffeineBeverage Class

```java
public abstract class CaffeineBeverage {
	
    final void prepareRecipe() { // 서브클래스에서 이 메소드를 오버라이드해서 아무렇게나 
                                 // 음료를 만들지 못하도록 final로 선언해줍니다.
        boilWater();
        brew(); 
        pourInCup();
        addCondiments();
    }
    
    void boilWater() {
        System.out.println("물을 끓이는 중");
    }
    
    abstract void brew();           // Coffee와 Tea에서 이 메소드를 서로 다른 방식으로 
    abstract void addCondiments();  // 처리하기 때문에 추상 메소드로 선언해줍니다.
    
    void pourInCup() {
        System.out.println("컵에 따르는 중");
    }
    
}
```

#### Tea Class

```java
public class Tea extends CaffeineBeverage {
	public void brew() {
		System.out.println("차를 우려내는 중");
	}
	
	public void addCondiments() {
		System.out.println("레몬을 추가하는 중");
	}
}
```

#### Coffee Class

```java
public class Coffee extends CaffeineBeverage {
	public void brew() {
		System.out.println("필터로 커피를 우려내는 중");
	}
	
	public void addCondiments() {
		System.out.println("설탕과 커피를 추가하는 중");
	}
}
```

**이처럼 `Template Method Pattern` 에서는 알고리즘의 각 단계들을 정의하며, 그 중 한 개 이상의 단계가 서브클래스에 의해 제공될 수 있습니다.**

<br/>

## Template Method Pattern의 사용 이점

- CoffeineBeverage 클래스에서 작업을 처리합니다. 알고리즘을 혼자 독점하고 있습니다.
- CoffeineBeverage 덕분에 서브클래스에서 코드를 재사용할 수 있습니다.
- 알고리즘은 한 군데에 모여 있기 때문에 그 부분만 고치면 됩니다.
- Template Method Pattern을 사용하는 버전에서는 다른 카페인 음료도 쉽게 추가할 수 있는 프레임워크를 제공합니다. 카페인 음료를 추가할 때 몇 가지 메소드만 추가하면 됩니다.
- CaffeineBeverage 클래스에 알고리즘에 대한 지식이 집중되어 있으면 일부 구현만 서브클래스에 의존합니다.

<br/>

## Template Method Pattern과 Hook

후크(hook)는 추상 클래스에서 선언되는 메소드긴 하지만 기본적인 내용만 구현되어 있거나 아무 코드도 들어있지 않은 메소드입니다. 이렇게 하면 서브클래스 입장에서는 다양한 위치에서 알고리즘에 끼어들 수 있습니다. 

후크는 다양한 용도로 사용할 수 있는데 우선 한가지 사용법을 살펴보겠습니다.

#### CaffeineBeverage Class

```java
public abstract class CaffeineBeverageWithHook {
    void prepareRecipe() {
        boilWater();
        brew(); 
        pourInCup();
        
        if(customerWantsCondiments()){
        	addCondiments();    
        }
    }
    
    void boilWater() {
        System.out.println("물을 끓이는 중");
    }
    
    abstract void brew();          
    abstract void addCondiments(); 
    
    void pourInCup() {
        System.out.println("컵에 따르는 중");
    }
    
    boolean customerWantsCondiments() { // 이 메소드는 서브클래스에서 필요에 따라 
        return true;                    // 오버라이드 할 수 있는 메소드이므로 후크입니다.
    }
}
```

이 후크를 사용하려면, Coffee나 Tea와 같은 서브클래스에서 필요에 따라 `customerWantsConidments()` 를 오버라이드해서 음료에 첨가물을 추가할지 여부를 결정할 수 있습니다.

<br/>

## 헐리우드 원칙

헐리우드 원칙은 디자인 원칙으로 `먼저 연락하지 마세요. 저희가 연락드리겠습니다.` 입니다.

헐리우드 원칙을 활용하면 `의존성 부패(dependency rot)` 를 방지할 수 있습니다. 의존성 부패는 구성요소 간의 의존성이 복잡하게 꼬여있는 것을 의하는데, 이렇게 의존성이 부패하면 시스템이 어떤 식으로 디자인된 것인지 거의 아무도 알아볼 수 없게 됩니다.

헐리우드 원칙을 사용하면, 저수준 구성요소에서 시스템에 접속을 할 수는 있지만, 언제 어떤 식으로 그 구성요소들을 사용할지는 고수준 구성요소에서 결정하게 됩니다. 즉, 고수준 구성요소에서 저수준 구성요소에게 "먼저 연락하지마세요. 제가 먼저 연락드리겠습니다." 라고 얘기를 하는 것과 같습니다.

<br/>

## 헐리우드 원칙과 Template Method Pattern

위의 예제에서 설명하자면, CaffeineBeverage는 고수준 구성요소입니다. 음료를 만드는 방법에 해당하는 알고리즘을 장악하고 있고, 메소드 구현이 필요한 상황에서만 서브클래스를 불러냅니다.

서브클래스는 자질구레한 메소드 구현을 제공하기 위한 용도로만 사용됩니다. 

CaffaeineBeverage 클래스의 클라이언트에서는 Tea나 Coffee 같은 구상 클래스가 아닌 CaffeineBeverage에 추상화되어 있는 부분에 의존하게 됩니다. 그렇게 함으로써 전체 시스템의 의존성이 줄어들 수 있습니다.

이 밖에도 헐리우드 원칙을 사용하는 디자인 패턴에는 **Factory Method Pattern** , **Observer Pattern** 등이 있습니다.

<br/>

## Conclusion

Template Method Pattern은 프레임워크를 만드는 데 아주 훌륭한 디자인 도구라고 합니다. 프레임워크를 사용함으로써 작업이 처리되는 방식은 제어할 수 있으면서도, 프레임우크에서 처리하는 알고리즘의 각 단계는 그 프레임워크를 사용하는 사람 마음대로 지정할 수 있기 때문입니다. 

Template Method Pattern와 Strategy Pattern은 상당히 유사해보이는데, 분명한 차이가 있습니다. 이 부분에 대해서는 추후 정리해보겠습니다. 

<br/>

## Reference & Additional Resources

- HeadFirstDesignPattern

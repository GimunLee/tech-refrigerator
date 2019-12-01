# Upcasting & Downcasting

*Assembled by GimunLee (2019-11-19)*

<br>

## Goal

- Upcasting과 Downcasting에 대해 설명할 수 있다.

<br>

## Casting (강제 형변환, 명시적 형변환)

**캐스팅(casting)** 이란 타입을 변환하는 것을 말하며 **형변환** 이라고도 합니다. 자바의 상속 관계에 있는 부모와 자식 클래스 간에는 서로 간의 형변환이 가능합니다.

이번 글에서는 자식 클래스가 부모 클래스의 타입으로 캐스팅되는 업캐스팅과 반대로 부모 클래스가 자식 클래스의 타입으로 캐스팅되는 다운캐스팅에 대해서 정리합니다. 시작하기에 앞서 부모 클래스인 상속 관계의 상위 클래스를 **수퍼 클래스** , 그리고 자식 클래스인 하위 클래스를 **서브 클래스** 라고 정의합니다.

간단하게 말하자면 **자료형이 정해진 변수에 값을 넣을때는, 변수가 원하는 정보를 하나도 빠짐 없이 다 넣어줘야 성립합니다.**

<br>

## Upcasting

자바에서 서브 클래스는 수퍼 클래스의 모든 특성을 상속받습니다. 그렇기 때문에 서브 클래스는 수퍼 클래스로 취급될 수 있습니다. 여기서 **Upcasting** 이란 서브 클래스의 객체가 수퍼 클래스 타입으로 형변환되는 것을 말합니다.

즉, 수퍼 클래스 레퍼런스 변수가 서브 클래스로 객체화된 인스턴스를 가리킬 수 있게 됩니다. 

```java
class Parent {
    String parentValue;

    public Parent(String parentValue) {
        this.parentValue = parentValue;
    }
    
    public void print() {
    	System.out.println("Parent 호출");
    }
}

class Child extends Parent {
    String childValue;

    public Child(String parentValue) {
        super(parentValue);
    }
    
    @Override
    public void print() {
    	System.out.println("Child 호출");
    }
}

public class UpcastingTest {
    public static void main(String[] args) {
        Child child = new Child("부모값 채우기");
        child.childValue = "자식값 채우기"; // OK

        Parent parent = child;
        parent.parentValue = "부모값 채우기"; // OK
        
        parent.childValue = "자식값 채우기"; // 컴파일 에러 발생
        
        parent.print(); // "Child 호출"이 출력됩니다.
    }
}
```

위 코드에서 `parent` 레퍼런스 변수는 Child 객체를 가리키고 있으며 `Parent type`이기 때문에 오로지 자신의 클래스에 속한 멤버만 접근이 허용됩니다. 따라서 childValue 멤버는 `Child type`의 멤버이므로 컴파일 시점에 오류가 발생합니다.

이처럼 업캐스팅을 하게되면 객체 내에 있는 모든 멤버에 접근할 수 없습니다. 오직 수퍼 클래스의 멤버에만 접근이 가능합니다. 이는 필드뿐만 아니라 **메서드(Method)에도 동일하게 적용됩니다.**

위의 코드에서처럼 업캐스팅 시에는 아래와 같이 명시적인 타입 캐스팅 선언을 하지 않아도 됩니다. 서브 클래스 Child는 Parent 타입이기 때문에도 그렇습니다. 이렇게 Upcasting을 사용하는 이유는 **다형성(Polymorphism)** 과 관련이 있는데, 다른 장에서 알아보도록 하겠습니다.

<br>

## Downcasting

**Downcasting** 은 자신의 고유한 특성을 잃은 서브 클래스의 객체를 다시 복구 시켜주는 것을 말합니다. 즉, Upcasting 된 것을 다시 원상태로 돌리는 것을 말합니다.

```java
class Parent {
    String parentValue;

    public Parent(String parentValue) {
        this.parentValue = parentValue;
    }
}

class Child extends Parent {
    String childValue;

    public Child(String parentValue) {
        super(parentValue);
    }
}

public class DowncastingTest {
    public static void main(String[] args) {
        Parent parent = new Child("부모값 채우기"); // Upcasting

        Child child = (Child) parent; // Downcasting

        child.parentValue = "부모값 채우기"; // OK

        child.childValue = "자식값 채우기"; // OK
    }
}
Java
```

여기서 업캐스팅과 다른 점은 명시적으로 타입을 지정해야 한다는 점입니다. 그리고 업캐스팅이 선행이 되어야 하는데요. 다운캐스팅을 하면서 형변환할 대상을 지정했지만 무분별한 다운캐스팅은 컴파일 시점에는 오류가 발생하지 않지만 런타임 오류를 발생시킬 가능성이 있습니다.

예를 들어 아래와 같이 진행하는 경우는 실행중 오류가 발생합니다.

```java
Child child = (Child) new Parent("부모값 채우기");
```

따라서 형변환할 타입을 명시함으로서 컴파일 오류는 사라졌지만 실제 코드를 수행하면 런타임 시, `ClassCastException`이 발생하게 됩니다. 

이렇게 혼동되는 객체를 구별하기 위해 도움을 주는 `instanceof` 연산자가 있습니다.

<br>

## Reference & Additional Resources

-  https://madplay.github.io/post/java-upcasting-and-downcasting 
-  https://mommoo.tistory.com/41 
-  https://mommoo.tistory.com/51 


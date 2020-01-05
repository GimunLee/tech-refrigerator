# 제네릭(Generic)

*Assembled by GimunLee (2020-01-04)*

<br/>

## Goal

- 제네릭에 대해 설명할 수 있다.

- 제네릭 사용 이점에 대해 설명할 수 있다.
- 제네릭 타입 변수를 제한할 수 있다.
- 제네릭 와일드 카드에 대해서 설명할 수 있다.

<br/>

## 제네릭(generic)이란?

자바에서 **제네릭이란 데이터의 타입을 일반화한다(generalize)** 는 것을 의미합니다.

제네릭은 클래스나 메소드에서 사용할 내부 데이터 타입을 컴파일 시에 미리 지정하는 방법입니다. 이렇게 컴파일 시에 미리 타입 검사(type check)를 수행하면 다음과 같은 장점을 가집니다.

1. **컴파일 시 강한 타입 체크를 통해,** 클래스나 메소드 내부에서 사용되는 객체의 타입 안정성을 높일 수 있습니다.
2. 반환값에 대한 타입 변환 및 타입 검사에 들어가는 노력을 줄일 수 있습니다.
3. 타입 변환을 제거해 전체 애플리케이션 성능을 높일 수 있다.

JDK 1.5 이전에서는 여러 타입을 사용하는 대부분의 클래스나 메소드에서 인수나 반환값으로 Object 타입을 사용했습니다. 하지만, 이 경우에는 반환된 Object 객체를 다시 원하는 타입으로 타입 변환해야 하며, 이때 오류가 발생할 가능성도 존재합니다.

JDK 1.5부터 도입된 제네릭을 사용하면 **컴파일 시에 미리 타입이 정해지므로,** 타입 검사나 타입 변환과 같은 번거로운 작업을 생략할 수 있게 됩니다.

<br/>

## 제네릭 사용 비교

### 제네릭 사용 전

```java
List list = new ArrayList();
list.add("hello");
String str = (String) list.get(0);
```

위의 코드에서는 강제타입 변환이 두번 일어납니다.

"hello"라는 String 객체를 Object 타입으로 저장할 때 한번, list.get(0)의 반환값인 Object 타입의 객체를 String 타입으로 저장할 때 한번. 제네릭을 적용하면 다음과 같이 코드가 변화합니다.

### 제네릭 사용 후

```java
List<String> list = new ArrayList<String>();
list.add("hello");
String str = list.get(0);
```

List 객체를 생성할 때, String 객체를 저장하겠다고 선언하면 불필요한 타입변환이 사라지게 됩니다.

<br/>

## 제네릭의 선언 및 생성

자바에서 제네릭은 클래스와 메소드에만 다음과 같은 방법으로 선언할 수 있습니다.

```java
class MyArray<T> {
    T element;
    void setElement(T element) { this.element = element; }
    T getElement() { return element; }
}
```

위의 예제에서 사용된 'T'를 **타입 변수(type variable)** 라고 하며, 임의의 참조형 타입을 의미합니다.

꼭 'T'뿐만 아니라 어떠한 문자를 사용해도 상관없으며, 여러 개의 타입 변수는 쉼표(,)로 구분하여 명시할 수 있습니다. 타입 변수는 클래스에서뿐만 아니라 메소드의 매개변수나 반환값으로도 사용할 수 있습니다. 

위와 같이 선언된 제네릭 클래스(generic class)를 생성할 때에는 타입 변수 자리에 사용할 실제 타입을 명시해야 합니다.

```java
MyArray<Integer> myArr = new MyArray<Integer>();
```

위의 예제는 MyArray 클래스에 사용된 타입 변수로 Integer 타입을 사용하는 예제입니다. 위처럼 제네릭 클래스를 생성할 때 사용할 실제 타입을 명시하면, 내부적으로는 정의된 타입 변수가 명시된 실제 타입으로 변환되어 처리됩니다.

자바에서 타입 변수 자리에 사용할 실제 타입을 명시할 때 기본 타입을 바로 사용할 수는 없습니다. 이때는 위 예제의 Integer와 같이 래퍼(wrapper) 클래스를 사용해야만 합니다.

다음 예제는 제네릭에서 적용되는 타입 변수의 다형성을 보여주는 예제입니다.

```java
import java.util.*;

class LandAnimal { 
	public void crying() { 
		System.out.println("육지동물"); 
	} 
}

class Cat extends LandAnimal { 
	public void crying() { 
			System.out.println("냐옹냐옹"); 
		} 
	}

class Dog extends LandAnimal { 
	public void crying() { 
		System.out.println("멍멍"); 
	}
}

class Sparrow { 
	public void crying() { 
		System.out.println("짹짹"); 
	}
}

class AnimalList<T> {
    ArrayList<T> al = new ArrayList<T>();
    void add(T animal) { al.add(animal); }
    T get(int index) { return al.get(index); }
}

public class Generic01 {
  public static void main(String[] args) {
      AnimalList<LandAnimal> landAnimal = new AnimalList<>(); // Java SE 7부터 생략가능함.

      landAnimal.add(new LandAnimal());
      landAnimal.add(new Cat());
      landAnimal.add(new Dog());
      // landAnimal.add(new Sparrow()); // 오류가 발생함.
       	
      for (int i = 0; i < landAnimal.size() ; i++) {
        landAnimal.get(i).crying();
      }
  }
}
```

위의 예제에서 Cat과 Dog 클래스는 LandAnimal 클래스를 상속받는 자식 클래스이므로, AnimalList<LandAnimal>에 추가할 수 있습니다. 하지만 Sparrow 클래스는 타입이 다르므로 추가할 수 없습니다.

### 참고

제네릭에 쓰인 T V N 등의 알파벳 대문자은 **임의의 알파벳 대문자** 를 사용한 것입니다. 이렇게 제네릭에 알파벳 대문자를 임의로 사용할 수 있지만, 그래도 일종의 약속이 있는데, 주로 아래와 같은 의미로 사용됩니다.

- `E` : Element

- `K` : Key

- `N` : Number

- `T` : Type

- `V` : Value

<br/>

## 제네릭의 제거 시기

자바 코드에서 선언되고 사용된 제네릭 타입은 컴파일 시 컴파일러에 의해 자동으로 검사되어 타입 변환됩니다. 그리고서 코드 내의 모든 제네릭 타입은 제거되어, 컴파일된 class 파일에는 어떠한 제네릭 타입도 포함되지 않게 됩니다. 이런 식으로 동작하는 이유는 제네릭을 사용하지 않는 코드와의 호환성을 유지하기 위해서입니다.

<br/>

## 타입 변수의 제한

제네릭은 'T'와 같은 변수(type variable)를 사용하여 타입을 제한합니다. 이때 extends 키워드를 사용하면 타입 변수에 특정 타입만을 사용하도록 제한할 수 있습니다.

```java
class AnimalList<T extends LandAnimal> {...}
```

위와 같이 클래스의 타입 변수에 제한을 걸어 놓으면 클래스 내부에서 사용된 모든 타입 변수에 제한이 걸립니다. 이때에는 **클래스가 아닌 인터페이스를 구현할 경우에도 implements 키워드가 아닌 extends 키워드를 사용해야만 합니다.**

```java
interface WarmBlood { ... }
...
class AnimalList<T extends WarmBlood> { ... } // implements 키워드를 사용해서는 안됨.
```

클래스와 인터페이스를 동시에 상속받고 구현해야 한다면 엠퍼센트(&) 기호를 사용하면 됩니다.

```java
class AnimalList<T extends LandAnimal & WarmBlood> {...}
```

<br/>

## 제네릭 메소드(generic method)

제네릭 메소드란 메소드의 선언부에 타입 변수를 사용한 메소드를 의미합니다. 이때 타입 변수의 선언은 메소드 선언부에서 반환 타입 바로 앞에 위치합니다.

```java
public static <T> void sort(...) {...}
```

다음 예제의 제네릭 클래스에서 정의된 타입 변수 T와 제네릭 메소드에서 사용된 타입 변수 T는 전혀 별개의 것임을 주의합니다.

```java
class AnimalList<T> {
	public static <T> void sort(List<T> list, Comparator<? super T) comp){
		...
	}
	...
}
```

### 실습 예제

```java
public class Pair<K, V> {
  private K key;
  private V value;

  public Pair(K key, V value) {
    this.key = key;
    this.value = value;
  }
	// getter, setter 생략
}
```

```java
public class Util {
  public static <K, V> boolean compare(Pair<K, V> p1, Pair<K, V> p2) {
    boolean keyCompare, valueCompare;

    keyCompare = p1.getKey().equals(p2.getKey());
    valueCompare = p1.getValue().equals(p2.getValue());

    return keyCompare && valueCompare;
  }
}
```

```java
public class CompareMethodEx {
  public static void main(String[] args) {
    Pair<String, Integer> p1 = new Pair<>("홍길동", 10);
    Pair<String, Integer> p2 = new Pair<>("홍길동", 10);

    boolean result = Util.compare(p1, p2);
    System.out.println(result); // true

    Pair<String, String> p3 = new Pair<>("홍길동", "홍길동");
    Pair<String, String> p4 = new Pair<>("홍길동", "춘향이");

    result = Util.compare(p3, p4);
    System.out.println(result); // false
  }
}
```

<br/>

## 와일드카드의 사용

와일드카드란 이름에 제한을 두지 않음을 표현하는 데 사용되는 기호를 의미합니다. 자바의 제네릭에서는 물음표(?) 기호를 사용하여 이러한 와일드카드를 사용할 수 있습니다.

```java
<?>           // 타입 변수에 모든 타입을 사용할 수 있음
<? extends T> // T 타입과 T 타입을 상속받는 자손 클래스 타입만을 사용할 수 있음
<? super T>   // T 타입과 T 타입이 상속받은 조상 클래스 타입만을 사용할 수 있음
```

###  와일드카드 제한

API를 잘 살펴보면 `T, E, S, V` 등으로 선언된 것도 있고 `?` 로 선언된 것도 있습니다.  `T`로  선언하는 것과 달리 `?` 로 선언했을 때는 제한이 있습니다. 데이터보다 메소드에 집중할 때 사용됩니다.

### 제네릭 vs 와일드카드

간단하게 말하자면, 아래와 같습니다.

**제네릭** : 지금은 이 타입을 모르지만, 이 타입이 정해지면 그 타입 특성에 맞게 사용하겠다!
**와일드 카드** : 지금도 이 타입을 모르고, 앞으로도 모를 것이다!

아래에서 예시를 통해, 좀더 자세히 알아보겠습니다.

**`List<?> list `**

- 원소를 꺼내 와서는 Object에 정의되어 있는 기능만 사용하겠다. `equals(), toString(), hashCode() ...`
- List에 타입이 뭐가 오든 상관 없다. 나는 List 인터페이스에 정의되어 있는 기능만 사용하겠다. `size(), clear() ...` 
- 단, 타입 파라미터와 결부된 기능은 사용하지 않겠다.  `add(), addAll()`

**``List<T> list``** 

- 원소를 꺼내 와서는 Object에 정의되어 있는 기능만 사용하겠다. `equals(), toString(), hashCode() ...`
- List에 타입이 뭐가 오든 상관 없다. 나는 List 인터페이스에 정의되어 있는 기능을 사용하고, 타입 파라미터와 결부된 기능도 사용하겠다.

```java
@Test
public void sampleCode2() { 
  List<Integer> integerList = Arrays.asList(1, 2, 3); 
  printList1(integerList);
  printList2(integerList);
} 

static void printList1(List<?> list) { 
  // 1. 와일드 카드는 list에 담긴 원소에는 전혀 관심이 없기 때문에 원소와 관련된 add 메소드를 사용할 수 없음
  // 2. 단, null은 들어갈 수 있음
  list.add(list.get(1)); // 컴파일 실패
} 

static <T> void printList2(List<T> list) { 
  // 1. 제네릭은 list에 담긴 원소에 관심을 갖기 때문에 원소와 관련된 add 메소드를 사용할 수 있음 
  // 2. 당연히 null도 들어갈 수 있음
  list.add(list.get(1)); // 컴파일 성공 
}

```

이렇게 보면, 제네릭과 와일드카드가 서로 대조적으로 쓰이는 것 같지만, 많은 API에서는 서로 혼합해서 확장성을 높히는 쪽으로 활용합니다. 

<br/>

## Reference & Additional Resources

- https://vvshinevv.tistory.com/55
- http://tcpschool.com/java/java_generic_concept
- https://ict-nroo.tistory.com/42
- https://preamtree.tistory.com/138




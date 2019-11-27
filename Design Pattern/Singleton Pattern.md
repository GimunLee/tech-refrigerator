# 🍐☝️ Singleton Pattern

*Assembled by Anna (2019-11-27)*

<br/>

## Goal

- Singleton Pattern 의 개념을 알 수 있다.
- Singleton Pattern 을 동작원리를 이해할 수 있다.
- Multi-thread 환경에서의 Singleton Pattern을 이해할 수 있다.

<br/>

## What is Singleton?

> Creating **one-of-a-kind objects** for which there is **only one instance**

단 `하나의 객체` 를 생성하고 생성된 객체를 어디서든 참조할 수 있도록 하는 패턴입니다.

여기서 주의할 점은 클래스를 static으로 선언하는 것이 아닌, 동적으로 생성하고 heap 영역에서 GC로 관리되도록 하되, 단 하나의 객체를 생성하는 것입니다. 

<br/>

## Singleton 구현과 사용

### Singleton 구현 방법

Singleton을 간단히 구현하면 다음과 같이 나타낼 수 있습니다.

```java
public class Singleton {
    private static Singleton instance; // 2
    private Singleton() {} // 1
    public static Singleton getInstance() // 3
        if(instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

1. **생성자**

   생성자를 `private` 지정자를 사용하여 외부 클래스에서 생성하지 못하도록 합니다.

2. **instance**

   Singleton의 객체입니다. 외부 클래스에서는 해당 객체를 사용하게 됩니다. 마찬가지로 `private` 지정자를 사용하여 외부 클래스에서 직접적으로 접근하지 못하게 합니다.

3. **getInstance()**

   외부의 모든 클래스에서 호출하여 Singleton 객체를 사용할 수 있습니다.

   1. 호출을 하게되면, 먼저 객체가 생성되었는 지를 판별합니다.
   2. 생성되지 않았다면, instance에 Singleton 객체를 생성하여 넣어줍니다.
   3. instance를 반환합니다.

### Singleton 사용

외부 클래스에서 다음과 같이 Singleton 객체를 사용할 수 있습니다.

```java
public class AnotherClass {
    void usingSingleton() {
        Singleton inst = Singleton.getInstance();
    }
}
```

<br/>

## Multi-Thread 환경에서의 Singleton

만약, Multi-thread 환경에서 두 개 이상의 스레드가 getInstance() 함수에 진입한다고 할 때 두 개 이상의 객체가 생성될 수 있습니다.

### 해결방법

1. **미리 인스턴스를 생성하는 방법.**

   ```java
   public class Singleton {
       private static Singleton instance = new Singleton();
       private Singleton() {}
       public static Singleton getInstance()
           return instance;
       }
   }
   ```

   > 미리 인스턴스를 생성하게 되면, 불필요한 시스템 리소스를 낭비하게 될 수도 있습니다.

2. **`synchronized` 를 사용하는 방법.**

   ```java
   public class Singleton {
       private static Singleton instance;
       private Singleton() {}
       public synchronized static Singleton getInstance()
           if(instance == null) {
               instance = new Singleton();
           }
           return instance;
       }
   }
   ```

   > getInstance() 메소드를 동기화하는 방법으로, 동기화로 인해 수행 시간이 느려진다는 단점이 있습니다.

3. **내부 `static` 클래스를 사용하는 방법.**

   ```java
   public class Singleton {
       private Singleton() {}
       public static Singleton getInstance() {
           return LazyHolder.INSTANCE;
       }
       // LazyHolder 기법 사용.
   	private static class LazyHolder {
       	private static final Singleton INSTANCE = new Singleton();
   	}
   }
   ```

   > `LazyHolder` 클래스는 `getInstance()` 가 호출되는 순간 Class가 로딩되며, 이 순간은 thread-safe 가 보장되기 때문에, `syncronized` 나 `volatile` 를 사용하지 않고도 안전하게 사용가능합니다.

<br/>

## Reference & Additional Resources

- <https://jungwoon.github.io/java/2019/08/11/Singleton-Pattern-with-Multi-Thread/>
- HeadFirstDesignPattern



 


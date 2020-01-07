# Java Lamda Expression (기초)

*Assembled by GimunLee*

<br/>

## Goal

- 람다식의 필요성에 대해 설명할 수 있다.
- 람다식을 사용할 수 있다.
- 람다식의 장점에 대해 설명할 수 있다.

<br/>

## 람다식(Lamda Expression)

람다식은 다른말로 **익명 메소드** 라고도 합니다.

- 인터페이스 중에서 메소드를 하나만 가지고 있는 인터페이스를 **함수형 인터페이스** 라고 합니다. 
  - 쓰레드를 만들때 사용하는 Runnable 인터페이스의 경우 run() 메소드를 하나만 가지고 있습니다.

#### Runnable을 이용하여 "hello"를 10번 찍는 쓰레드를 만드는 방법

```java
public class LambdaExam1 {
	public static void main(String[] args) {
		new Thread(new Runnable(){
      public void run(){
        for(int i = 0; i < 10; i++){
          System.out.println("hello");
        }
      }
    }).start();
  }   
}
```

- 쓰레드가 실행되면 쓰레드 생성자 안에 넣은 run() 메소드가 실행됩니다.
- 자바는 메소드만 매개변수로 전달할 방법이 없습니다. 인스턴스만 전달 할 수 있습니다.
- 그렇기 때문에 run()메소드를 가지고 있는 Runnable 객체를 만들어서 전달합니다.

*메소드만 전달할 수 있다면, 좀더 편리하게 프로그래밍할 수 있을텐데, **자바는 메소드만 전달할 수 있는 방법은 없었기기 때문에 매번 객체를 생성해서 매개변수로 전달해야 했습니다.** 이런 부분을 해결한 것이 람다 표현식입니다.*

#### 람다식을 이용해서 수정한 코드

```java
public class LambdaExam1 {  
  public static void main(String[] args) {
    new Thread(() -> {
      for(int i = 0; i < 10; i++){
        System.out.println("hello");
      }
    }).start();
  }   
}
```

- `() -> { ..... }` 부분이 람다식, 다른말로 익명 메소드입니다.
- JVM은 Thread 생성자를 보고 `() -> {}` 이 무엇인지 대상을 추론합니다.
- Thread 생성자 api를 보면 Runnable 인터페이스를 받아들이는 것을 알 수 있습니다.
- JVM은 Thread 생성자가 Runnable 인터페이스를 구현한 것이 와야 하는 것을 알게 되고, `() -> { ..... }` 을 Runnable을 구현하는 객체로 자동으로 만들어서 매개변수로 넣어줍니다.

<br/>

## 람다식(Lamda Expression) 기본문법

`(매개변수목록) -> {실행문}`

- Compare 인터페이스

  - 2개의 값을 받아들인 후, 정수를 반환하는 compareTo() 메소드를 선언

  ```java
  public interface Compare{
    public int compareTo(int value1, int value2);
  }
  ```

- Compare 인터페이스를 이용하는 클래스

  - Compare 인터페이스를 받아들인 후, 해당 인터페이스를 이용하는 exec() 메소드
  - compareTo 메소드가 어떻게 구현되어 있느냐에 따라서 출력되는 값이 다릅니다.

  ```java
  public class CompareExam {      
  	public static void exec(Compare Compare){
      int k = 10;
      int m = 20;
      int value = Compare.compareTo(k, m);
      System.out.println(value);
    }
    
    public static void main(String[] args) {    
      exec((value1, value2)->{
        return value1 - value2;
      }); 
    }
  }
  ```

*자바는 메소드만 인자로 전달하려면 반드시 객체를 만들어서 전달해야 했습니다. 하지만, Java 8에 람다식이 생기면서, 마치 함수만 전달하는 것처럼 간편하게 문법을 사용할 수 있게 됐습니다.*

<br/>

## Reference & Additional Resources

- https://programmers.co.kr/learn/courses/9
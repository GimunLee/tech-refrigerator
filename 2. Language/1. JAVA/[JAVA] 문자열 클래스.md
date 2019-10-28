### [JAVA] 문자열 클래스

---

*Assembled by Ricky (2019-10-28)*

- #####  Introduction

  -  JAVA에는 문자열 클래스로 String, StringBuffer, StringBuilder 3가지가 있습니다. 사소해보이지만 상황에라 어떤 클래스를 쓰냐에 따라, 성능차이가 발생하는데요. 어떤 차이점이 있는지 알아보도록 하겠습니다. 

<br>

- ##### Body

  - **```String vs StringBuffer vs StringBuilder```**

    | Index        | String        | StringBuffer | StringBuilder |
    | ------------ | ------------- | ------------ | ------------- |
    | Storage Area | Heap          | Heap         | Heap          |
    | Modiifable   | No(immutable) | Yes(mutable) | Yes(mutable)  |
    | Thread-Safe  | YES           | YES          | NO            |
    
    - String과 다른 클래스(StringBuffer, StringBuilder)의 기본적인 차이는 String은 Immutable(불변), StringBuffer, StringBuilder는 Mutable(가변)에 있습니다.
    
  - **```String Class```**
  
    - String 객체는 한번 생성되면 할당된 메모리 공간이 변하지 않습니다. 즉, '+' 연산 또는 concat 메서드를 통해 기존에 생성된 String 객체에 다른 문자열을 붙여도 기존 문자열에 새로운 문자열을 붙이는 것이 아닙니다. 새로운 String 객체를 만든 후, 이 객체에 연결된 문자열을 저장하고, 그 객체를 참조하도록합니다. 
    - 장점
      - String Class의 객체는 Immutable(불변)하기 때문에 단순하게 읽어가는 조회 연산에서는 타 클래스보다 빠르게 읽을 수 있습니다.
      - Immutable(불변)하기 때문에 멀티쓰레드 환경에서 동기화를 신경 쓸 필요가 없습니다. (Thread-Safe)
    - 단점
      - 문자열 연산('+', concat 등)을 많이 일어나는 경우, 더이상 참조되지 않는 기존 객체는 Garbage Collection(이하, GC)에 의해 제거되야하기 때문에 성능이 좋지 않습니다.
  
  - **```StringBuffer와 StringBuilder Class```**
  
    - 
    - 

<br> 

- ##### Conclusion

  - 

<br>

- ##### Reference & Additional Resources

  -  https://cjh5414.github.io/why-StringBuffer-and-StringBuilder-are-better-than-String/ 
  -  https://novemberde.github.io/2017/04/15/String_0.html 
  -  https://jeong-pro.tistory.com/85 
  -  https://12bme.tistory.com/42 
  -  https://itblackbelt.wordpress.com/2015/01/31/difference-between-string-stringbuilder-and-stringbuffer-classes-with-example-java/ 

---






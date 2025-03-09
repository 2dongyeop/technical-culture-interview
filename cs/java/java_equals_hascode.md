## Java의 Object 클래스의 Equals() 메서드와 HashCode() 메서드가 무슨 목적인지 설명해주세요.

### equals()와 hashCode()의 목적

- `Object` 클래스에서 제공하는 `equals()`와 `hashCode()` 메서드는 객체의 동등성을 비교하고, 해시 기반 자료구조에서 올바르게 동작하기 위해 필수적입니다.
- `equals()` : 두 객체의 **내용(값)** 이 같은지를 비교
- `hashCode()` : 객체를 해시 **기반 자료구조(HashMap, HashSet 등)** 에서 효율적으로 관리하기 위한 해시값을 반환

### equals() 메서드 (객체 동등성 비교)

- Java의 Object.equals() 메서드는 기본적으로 "참조 비교(reference equality)"를 수행합니다.

    ```java
    
    @Override
    public boolean equals(Object obj) {
        return (this == obj); // 동일한 객체(참조)인지 비교
    }
    ```

    - 즉, == 연산자와 같은 방식으로 동작하여 **두 개의 객체가 같은 메모리 주소를 가리킬 때만 true**를 반환합니다.

  ```java
  String a = new String("hello");
  String b = new String("hello");
  
  System.out.println(a ==b); // false (참조 비교)
  System.out.println(a.equals(b)); // true  (내용 비교)  → String은 equals()를 오버라이딩했기 때문!
  ```
    - String 클래스는 equals()를 오버라이딩하여 문자열 값을 비교하도록 구현되어 있습니다.

<br/>

### hashCode() 메서드 (해시 기반 자료구조에서 필수)

Java의 Object.hashCode() 메서드는 객체의 메모리 주소를 기반으로 한 해시값을 반환합니다.

```java

@Override
public native int hashCode();
```

- hashCode()가 필요한 이유
    - 해시 기반 자료구조 (HashMap, HashSet, HashTable)에서는 객체를 저장할 때 hashCode() 값을 사용하여 특정 버킷(bucket)에 저장합니다.
    - ➡ 같은 객체는 같은 hashCode() 값을 가져야 하고, 같은 내용의 객체라면 equals()가 true일 때 hashCode()도 동일해야 합니다.

<br/>

### 객체 동등성 비교가 필요한 이유

> 컬렉션에서 객체 중복 방지 (HashSet, HashMap 등)

해시 기반 자료구조(예: HashSet, HashMap)에서는 객체를 저장할 때 hashCode()와 equals()를 사용하여 중복을 방지합니다.

<br/>

#### 예제: equals()를 오버라이딩하지 않은 경우

- equals()를 오버라이딩하지 않았기 때문에, 동일한 name을 가진 객체도 다른 객체로 인식됩니다.
- 따라서 중복 방지를 위해 equals()를 오버라이딩해야 함.

```java
import java.util.HashSet;

class Person {
    String name;

    Person(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        HashSet<Person> set = new HashSet<>();
        set.add(new Person("Alice"));
        set.add(new Person("Alice"));

        System.out.println(set.size()); // 2 (중복 저장됨!)
    }
}
```

<br/>

> 객체 비교가 필요한 로직에서 사용 (리스트 검색, 정렬 등)

예를 들어, 리스트에서 특정 객체를 검색할 때 equals()가 올바르게 구현되어 있지 않으면 원하는 결과를 얻을 수 없습니다.

<br/>

#### 예제: equals() 미구현 시 검색 실패

- `contains()`는 내부적으로 equals()를 호출하여 객체를 비교합니다.
- `equals()`가 구현되지 않았으므로 내용이 같아도 다른 객체로 인식하여 검색이 실패합니다.

```java
import java.util.ArrayList;
import java.util.List;

class Person {
    String name;

    Person(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        List<Person> list = new ArrayList<>();
        list.add(new Person("Alice"));

        Person searchPerson = new Person("Alice");
        System.out.println(list.contains(searchPerson)); // false (찾지 못함)
    }
}
```

<br/>

> HashMap에서 Key 비교 (올바른 값 조회)

#### 예제: equals() 미구현 시 HashMap에서 값 조회 실패
- p1과 p2는 name이 같지만, hashCode()와 equals()가 정의되지 않아 다른 객체로 인식됩니다.
- 따라서 map.get(p2)에서 값을 찾지 못하고 null이 반환됩니다.

```java
import java.util.HashMap;

class Person {
    String name;

    Person(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        HashMap<Person, Integer> map = new HashMap<>();
        Person p1 = new Person("Alice");
        map.put(p1, 100);

        Person p2 = new Person("Alice");
        System.out.println(map.get(p2)); // null (조회 실패!)
    }
}
```


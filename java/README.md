# JAVA

## String Class

https://novemberde.github.io/2017/04/15/String_0.html

String 문자열이 변경되면 기존의 Object를 버리고 새로운 Object를 생성한다. 이때 기존 Object는 GC에 의해서 메모리 회수가 이루어진다.

StringBuffer와 StringBuilder는 새로운 Object를 생성하지 않고 기존 Object를 재활용한다.

StringBuffer는 Synchronized 기법을 사용함으로 안전성이 좀 더 높다

StringBuilder는 들어오는 대로 받기 때문에 속도가 가장 빠르다.

```java

// String
String str = "JAVA";

str = str + "WORLD";

// String Buffer

StringBuffer sf = new StringBuffer("JAVA");

sf.append("WORLD");

// sf.insert(offset, "~~~");
// sf.delete(start, end );

// String Builder

StringBuilder sb = new StringBuilder("JAVA");

sb.append("WORLD");

```

## Collections

### List

ArrayList

```java

ArrayList<String> list = new ArrayList<String>();

// add data
list.add("Hello");
list.add("JAVA");
list.add("World");

// offset
list.add(2, "Programming");

// set (change data)
list.set(1, "C");

// get
String str = list.get(2);

// remove
list.remove(2);

// clear (Object는 살아있음)
list.clear();

// check data
boolean b = list.isEmpty();

```

### Map

HashMap

```java

HashMap<Integer, String> map = new HashMap<Integer, String>();

// add
map.put(5, "Hello");
map.put(6, "JAVA");
map.put(7, "WORLD");


// replace
map.put(6, "C");

String str = map.get(5);

map.remove(5);

map.containsKey(7);

map.clear();

Boolean b = map.isEmpty();


```

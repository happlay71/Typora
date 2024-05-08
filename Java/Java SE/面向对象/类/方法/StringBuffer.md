StringBuffer 是 Java 中的一个类，用于处理字符串的可变（mutable）版本。它在内存中创建一个可变长度的字符串缓冲区，可以动态修改和操作字符串内容，而不会每次都生成新的字符串对象，从而提高了字符串的操作效率。这在需要频繁修改字符串内容的情况下非常有用。

*以下是 StringBuffer 的一些常见特性和用法：*

**可变性**： 与 String 不同，StringBuffer 的内容可以通过方法调用进行修改，包括插入、追加、删除、替换等操作，而不会创建新的字符串对象。

**线程安全**： StringBuffer 是线程安全的，多个线程可以同时访问和修改同一个 StringBuffer 对象。这使它在多线程环境中非常有用。然而，线程安全可能导致一些性能开销，因此如果不需要线程安全，可以考虑使用 StringBuilder。

**容量自动增长**： 当 StringBuffer 的容量不足以容纳新的字符序列时，它会自动增加其容量以适应更多字符。

**常用方法**： StringBuffer 提供了一系列方法，包括 append（追加字符串）、insert（在指定位置插入字符串）、delete（删除字符序列）、replace（替换字符序列）、reverse（反转字符串）等，以便进行各种字符串操作。

```java
StringBuffer sb = new StringBuffer("Hello");
sb.append(" World"); // 追加字符串
sb.insert(5, " Awesome"); // 在指定位置插入字符串
sb.delete(5, 13); // 删除指定范围的字符
sb.replace(6, 13, "Java"); // 替换指定范围的字符
sb.reverse(); // 反转字符串

System.out.println(sb.toString()); // 输出：avaJ dlroW

```


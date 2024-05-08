[TOC]

### 添加、删除、修改

```java
/*
Object put(Object key, Object value): 将指定key-value添加到（或修改）当前map对象中
void putAll(Map m): 将m中的所有key-value对存放到当前map中
Object remove(Object key): 移除指定key的key-value对，并返回value
void clear(): 清空当前map中的所有数据
*/
		Map map = new HashMap();
        // 添加
        map.put("AA", 123);
        map.put(45, 123);
        map.put("BB", 56);
        // 修改
        map.put("AA", 87);

        System.out.println(map);
		// {AA=87, BB=56, 45=123}

        Map map1 = new HashMap();
        map1.put("CC", 123);
        map1.put("DD", 123);

        map.putAll(map1);

        System.out.println(map);
		// {AA=87, BB=56, CC=123, DD=123, 45=123}

        // 移除
        Object value = map.remove("CC");
        System.out.println(value);
		// 123
        System.out.println(map);
		// {AA=87, BB=56, DD=123, 45=123}

		// 清空
        map.clear();
        System.out.println(map);
		// {}
```

### 元素查询

```java

 		Map map = new HashMap();
        map.put("AA", 123);
        map.put(45, 123);
        map.put("BB", 56);
		// Object get(Object key): 获取指定key对应的value
        System.out.println(map.get(45));

        boolean isExist = map.containsKey("BB");
		// boolean containsKey(Object value): 是否包含指定的key
        System.out.println(isExist);

        // 若多个值相同，则返回第一个
        isExist = map.containsValue(123);
		// boolean containsVaule(Object value): 是否包含指定的value
        System.out.println(isExist);
		
		// int size(): 返回map中key-value对的个数
        System.out.println(map.size());

		// boolean isEmpty(): 判断当前map是否为空
        System.out.println(map.isEmpty());

        Map map1 = new HashMap();
        map1.put("AA", 123);
        map1.put(45, 123);
        map1.put("BB", 56);

		// boolean equals(Object obj): 判断当前map和参数对象obj是否相等
        System.out.println(map.equals(map1));
```

### 元视图操作的方法：

```java

		Map map = new HashMap();
        map.put("AA", 123);
        map.put(45, 123);
        map.put("BB", 56);

		// Set keySet(): 返回所有key构成的Set集合
        Set set = map.keySet();
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }

		// Collection values(): 返回所有value构成的Collection集合
        Collection values = map.values();
        for (Object obj : values) {
            System.out.println(obj);
        }

		// Set entrySet(): 返回所有key-value对构成的Set集合
        Set entrySet = map.entrySet();
        Iterator iterator1 = entrySet.iterator();
        while (iterator1.hasNext()) {
            Object obj = iterator1.next();
            System.out.println(obj);

            Map.Entry entry = (Map.Entry) obj;
            System.out.println(entry.getKey() + "--->" + entry.getValue());
        }
```


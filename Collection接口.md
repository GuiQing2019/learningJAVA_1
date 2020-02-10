# Collection接口

## 1.0 内容

​	

| 内容           | 知识点                      | 掌握程度 |
| -------------- | --------------------------- | -------- |
| Collection接口 | Collection方法              |          |
|                | Collection 接口遍历         |          |
| List接口       | List方法                    |          |
|                | List遍历                    |          |
|                | ArrayList/Vector/LinkedList |          |
| 泛型           | 泛型概念                    |          |
|                | 泛型应用                    |          |



## 1.1 为什么要使用容器/集合	

传统数组作为容器使用时，存在两个不足：

1. 不能自动拓容
2. 数组没有自己特有的方法，在进行增删改操作时，需要额外的逻辑（特定方法）。

Collection只能存储引用数据类型，不能存储基本数据类型

Java集合框架提供了一套性能优良，使用方便的接口和类，它们位于java.util 包中

## 1.2 Collection方法

```java
/**
         * 容器的主要方法
         * 增 add/addAll
         * 删 clear/remove/removeAll/retainsAll
         * 改
         * 查 contains/containsAll/size/isEmpty
         */

		Collection c1=new ArrayList();
        c1.add(2);
        c1.add(5);
        c1.add(0);
        c1.add(3);
        c1.add(1);

        Collection c2=new ArrayList();
        c2.add("java");
        c2.add(1);
        c2.addAll(c1);
        System.out.println(c2);


        //删除
        // c1.clear();
        //c2.removeAll(c1);
        //c2.retainAll(c1);
        //System.out.println(c2);

        //查找
        System.out.println(c2.contains("java"));
        System.out.println(c2.containsAll(c1));
        System.out.println(c2.size());
        System.out.println(c1.isEmpty()); //查看是否为空
```

## 1.3 Collection方法的遍历



```java
public class Test0130 {
    public static void main(String[] args) {
        /**
         *
         *        遍历
         *
         */

        Collection c1 =new ArrayList();
        c1.add("c++");
        c1.add("apple");
        c1.add("bannan");
        c1.add("coco");
        c1.add("java");
        System.out.println(c1);

        //foreach 快速遍历
        //object：待遍历集合的类型
        //item:迭代遍历
        //c1:需要遍历的集合
        for (Object item:c1) {
            System.out.println(item.toString());
        }

        System.out.println("--------------");

        
        //通过迭代器迭代集合元素
        //调用迭代器方法
        Iterator iterator = c1.iterator();
        //看看迭代器方法是否有下一位元素
        while (iterator.hasNext()){
            //如果有则获取下一位元素值输出
            Object obj = iterator.next();
            System.out.println(obj.toString());
        }
        
        
        
        
        
 			//国外的写法，不用再for外创建Itertor 造成资源浪费。
        for (Iterator it2=c1.iterator(); it2.hasNext();){
            Object obj2 = it2.next();
            System.out.println(obj2);
        }

        

    }
}
```





## 2.1 List接口

List接口要求存储数据类型必须有序，不唯一（可重复）

List接口表示有序的集合，也成序列，提供了索引Index,可以通过Index对集合进行增删改查。

```java
 public static void main(String[] args) {
        /**
         * 增 addAll(index)/add/addAll
         * 删 remove(index)/clear/remove/removeAll/retainsAll
         * 改 set(index,element)
         * 查 get(index)/indexOf(从左往右)/lastIndexOf(从右往左)/contains/containsAll/size/isEmpty
         * 遍历 iterator/listIterator/listIterator(index)
         */

        List list=new ArrayList();

        list.add("java");
        list.add(0,"c++");

       List list1=new ArrayList();

       list1.add("a");
       list1.add("cd");
       list1.addAll(1,list);
        System.out.println(list1);


        //删除
        Object remove = list1.remove(0);
        System.out.println(remove);
        System.out.println(list1);

        //修改
        list.set(0,"oracle");
        System.out.println(list);


        //查找
        list.add("java");
        System.out.println(list);
        System.out.println(list.get(0));
        System.out.println(list.indexOf("java"));
        System.out.println(list.lastIndexOf("java"));

    }
```

## 2.2 List接口的遍历

List接口继承于Iterable,具有快速遍历的能力。

List接口定义了一个方法listIterator,用于返回一个序列迭代器

ListIterator 接口称为序列迭代器，允许开发者以某一方向（正向或者逆向）迭代序列 。

```java
 public static void main(String[] args) {

        List list =new ArrayList();
        list.add("java");
        list.add("mysql");
        list.add("tomcat");
        
        //快速遍历
        for (Object item: list) {
            System.out.println(item.toString());
        }

        System.out.println("---------------------");
        //迭代器
        for (Iterator it2=list.iterator();it2.hasNext();){
            Object obj = it2.next();
            System.out.println(obj);
        }


        System.out.println("---------------------");
        ListIterator listIterator=list.listIterator();
        //正向遍历
        while (listIterator.hasNext()) {

            System.out.println(listIterator.next().toString());
        }



        System.out.println("---------------------");


        //逆向遍历
       while (listIterator.hasPrevious()){
           Object obj = listIterator.previous();
           System.out.println(obj.toString());
       }

    }
```

## 3.1 数据结构

数据结构根据其内存中的结构可以分为顺序表，链表，栈，队列，二叉树，图等数据结构

### 3.1.1 顺序表

顺序表就是指一种线性结构的，有序的数据结构。根据其物理空间是否连续为由分为数组和链表。

数组：

1. 物理空间连续，逻辑空间连续
2. 通过索引读取速度快
3. 增删数据速度慢

链表：

1. 物理空间不连续，逻辑控件连续。
2. 通过索引读取速度慢
3. 增删数据速度快

### 3.1.2 栈

栈值允许从同一方向操作栈空间,以先进后出，后进先出存储数据。

![](..\collection\imgs\栈.png)

### 3.1.3 队列

按照一个方向操作队列，以一个方向入队列，另一个方向出队列。图二是双向队列

![](..\collection\imgs\队列.png)

![](..\collection\imgs\双向队列.png)



## 4.1 ArrayList

ArrayList是List接口的实现类，底层数据结构是数组的可变有序列表。

ArrayList是包装类，内部封装了一个数组Object[] elmentsData，默认容量是10个空间，当调用add方法时，首先确认容量，如果容量够，直接添加，否则，按照newCapacity= oldCapacity+ oldCapacity/2的规则扩容。

在实际开发过程中，一定要结合业务需求，适当的调用ensureCapacity(minCapacity)和trimToSize来提供拓容性能和节省拓容空间。

ArratList 是线程不安全的可变数组版本。



## 5.1 Vector

Vector 是List 接口的实现类，底层数据结构是数组的可变有序列表。Vector是线程安全的。

Vector是包装类，内部封装了一个数组Object[] elmentsData，默认容量是10个空间，当调用add方法时，首先确认容量，如果容量够，直接添加，否则，按照

```java
int newCapacity = oldCapacity +((capacityIncrement>0)? capacityIncrement : oldCapacity);
//capacityIncrement增量因子，如没有设置，则加一倍默认长度（oldCapacity）
```

的规则拓容。

> 总结ArrayList和Vector的异同：
>
> 同：
>
> 1. 都是List的实现类。
> 2. 都是可变有序列表。
>
> 异：
>
> 1. JDK出现不同， ArrayList出现是1.2， Vector出现是1.0
> 2. ArrayList线程不安全，Vector线程安全
> 3. 拓容规则不一样，ArrayList没有拓容因子，Vector有拓容因子

## 6.1 LinkedList

LinkedList是List的实现类，底层数据结构是链表。

以栈的形式操作linkedList

![](../Collection/imgs/LinkedList.png)

```java
 public static void main(String[] args) {
        //以栈的数据结构操作
        LinkedList list=new LinkedList();

        //入栈
        list.push("java");
        list.push("banana");
        list.push("apple");
        System.out.println(list);


        //出栈
        System.out.println(list.pop());
    }
```

jdk1.0有专门的类Stack表示栈操作，继承于Vector，其操作是线程安全



以队列来操作LinkedList

```java
public static void main(String[] args) {
        //以队列的数据结构操作
        LinkedList list=new LinkedList();

        //入队
        list.offer("java");
        list.offer("apple");
        list.offer("bannan");


        //出队
        list.poll();
        list.poll();
        list.poll();

        Object obj=list.poll();
        System.out.println(obj);

        //检查元素，获取第一个元素不删除。
        System.out.println(list.peek());
    }
```



双向队列操作

![](../Collection/imgs/双向队列操作.png)

```java
 public static void main(String[] args) {
        //以双向队列的数据结构操作
        LinkedList list=new LinkedList();

        //入队
        list.offerFirst("java");
        list.offerLast("c++");
        list.offerLast("mysql");
        System.out.println(list);

        //出队
        list.poll();//默认出头一个
        System.out.println(list);
        list.pollLast(); //出最后一个
        System.out.println(list);
        list.pollFirst();//出头一个
        System.out.println(list);

        //检查元素
        System.out.println(list.peekFirst());//检查首个
        System.out.println(list.peekLast()); //检查最后一个
    }
```

## 7.1 Iterator 和 ListIterator

```java
public static void main(String[] args) {
	ArrayList<String> list = new ArrayList<String>(); 
    list.add("apple"); 
    list.add("banana"); 
    list.add("coco");
    
	Iterator<String> it = list.iterator(); 
    while(it.hasNext()) { 
        String item = it.next(); 
        if (item.equals("banana")) {
            list.add("java"); 
        }
    }
	System.out.println(list);
		}
//运行产生异常java.util.ConcurrentModificationException
```

> java.util.ConcurrentModificationException 表示并发修改异常。在遍历集合时， 不能 向集合添加元素。
> 如果在遍历过程中，对集合进行增、修改等操作，可以使用 ListIterator 接口 

```java
public static void main(String[] args) {
    ArrayList<String> list = new ArrayList<String>();
    list.add("apple"); 
    list.add("banana"); 
    list.add("coco");
    
    ListIterator<String> it = list.listIterator();
    
    while(it.hasNext()) { 
        String item = it.next(); 
        if (item.equals("banana")) {
   			 // it.add("java");
   		 it.set("Banana");
    		}
    	}
   	 System.out.println(list);
    	}

```

> Iterator 和 ListIterator 的区别 
>
> Iterator 接口是遍历的父接口，集合同一迭代器，只提供了以只读、删除的方式遍历集合，其中 hasNext 用于返回是否有下一个元素，next 用于取出该元素。
>
> ListIterator 继承于 Iterator，称为序列迭代器，允许程序员按任一方向遍历列表(正向、 逆向、指定位置)遍历列表，且在迭代期间可以修改列表(add、set、remove)。其中
>
>  hasNext/next 
>
> hasPrevious/previout 
>
> add/set/remove 
>
> nextIndex/previousIndex



## 8.1 Set接口

Set接口允许集合中的元素无序，唯一。

Set接口常用方法

```java
public static void main(String[] args) {

        /*
         * 增: add/addALL
         * 删  clear/remove/removeAll/retainAll
         * 改
         * 查   contains/containsAll/isEmpty/size
         * 遍历 iterator
         */

        Set set=new HashSet();

        //增
        set.add("java");
        set.add("banna");

        Set set1=new HashSet();
        set1.add("c++");
        set1.add("apple");

        //将set集合中元素添加到set1中
        set1.addAll(set);
        
        
        
        //循环输出
        for (Object sets:set1){
            System.out.println(sets);
        }
        //迭代器输出
        Iterator iterator=set.iterator();
        while (iterator.hasNext()){
            Object next = iterator.next();
            System.out.println(next);
        }

    }
```

### 8.1.1 HashSet

Hashset 是 Set接口的实现类，底层数据结构是哈希表（散列）。

### 8.1.2 哈希表工作原理

​	![](..\Collection\imgs\hashset.png)

> 总结: 如果一个元素要添加到HashSet中，该元素必须存在HashCode，且提供equals方法（在Generate中生成）。



### 8.1.3 HashSet 存储自定义对象

```java
@Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Studen studen = (Studen) o;
        return age == studen.age &&
                Objects.equals(name, studen.name) &&
                gender == studen.gender;
    }

    @Override
    public int hashCode() {

        return Objects.hash(name, age, gender);
    }
```

HashSet 如果要存储自定义对象，必须重写hashcode()和equals().因为从Object继承过来的HashCode（内存地址）和equals（默认比内存地址）不能满足自定义对象的需要。

自定义重写hashcode和equals时，一定和类或对象属性值有关。

hashcode 不同，散列得到的地址可能相同，所以需要equals比较内容。

hashcode相同，散列得到的地址相同，也需要经过equals比较内容。

### 8.1.4 HashSet性能

1. 添加/删除元素时，效率高
2. 查询元素，效率高
3. 没有数组高

### 8.1.5 LinkedHashSet

LinkedHashSet 是Set 接口的实现类，底层数据结构是哈希表+链表。其中哈希表用于存储元素 ，链表用于维持添加次序。LInkedHashSet是有序的且是添加的次序。

因为LinkedHashSet 底层数据结构存储元素时也是哈希表，所以在存储自定义元素时一定要重写HashCode 和 equals。

### 8.1.6 TreeSet

TreeSet 是Set 接口的实现类，底层结构是平衡二叉树（子树左右层级相同）

![](..\Collection\imgs\平衡二叉树.png)

#### 8.1.6.1 TreeSet存储自定义对象

从二叉树工作原理来看，如果想向TreeSet中存储元素，必须要提供比较策略（Comparable<T>接口。）

比较策略有两种：内部比较策略和外部比较策略 。

#### 8.1.6.2 Comparable 接口

Comparable 接口也称内部比较器，当知道比较对象的源代码时，可以使用内部比较器Comparable接口，在compareTo中提供比较策略。

```java
 public int compareTo(Studen o) {
        //按照年龄升序如果年龄相同，按名称升序
        if (this.age==o.age){
            return this.name.compareTo(o.name);
        }else {
            return this.age - o.age;
        }

    }
```

其中this 表示要加入对象的年龄，o 表示根节点的年龄

#### 8.1.6.3 外部比较器 -----Compartor接口

当不能获取添加元素源代码时，此时可以考虑使用外部比较器Compartor接口，其中定义了自然排序的方法compare(),用于提供比较策略。



使用TreeSet时，需要在构造方法中传入一个自定的比较器 TreeSet(Comparator<? super E> comparator)

```java
public static void main(String[] args) {

        /**
         * 练习：按照字符串长度，升序排列。
         * o1为添加的元素，o2为根元素.
         */

        TreeSet<String> tr =new TreeSet<String>(new Comparator<String>() {
            @Override //匿名内部类
            public int compare(String o1, String o2) {
                return o1.length() - o2.length();
            }
        });
        tr.add("banana");
        tr.add("apple");
        tr.add("coco");

        System.out.println(tr);

    }
```

#### 8.1.6.4 性能

添加、删除元素效率差

查找元素效率差

## 9.1 Map接口

Map也是一种容器，其值以Key-value（键值对） 的形式存储，这个key-value 键值对，在Map 接口中成Entry<K,V>实体。



Map容器以key-value 键值对形式存储数据，一个键值对作为一个Entry存在，这种数据结构称为映射。一般而言，都是通过key去存储value

Map常用方法：

```java
 public static void main(String[] args) {
        /**
         * 增 put(key,value)/putAll()
         * 删 clear/remove(key)
         * 改
         * 查 get(Key)/containsKey/containsValue/isEmpty/size
         */
        Map<String,String> map =new HashMap<String, String>();


        //增
        map.put("A","apple");
        map.put("B","banana");

        Map<String,String> map1=new HashMap<String, String>();

        map1.putAll(map);
        System.out.println(map1);

        //删除
        String a = map.remove("A");
        System.out.println(a);
        System.out.println(map);

        //检查是否包含某个元素
        System.out.println(map.containsKey("A"));
        System.out.println(map.containsValue("banana"));

        
    }
```

> 总结：
>
> 1. 通过 Key-value 存储map
> 2. map是无序的，但可以通过简单的数字，字母作为Key，让map有序。在开发过程，让map有序的情况很少。 

实际开发：构建一个有序的通讯录

```java
public static void main(String[] args) {
        ArrayList<String> list=new ArrayList<String>();
        Map<String,ArrayList> map=new HashMap<String, ArrayList>();

        list.add("alex");
        list.add("apx");
        list.add("aqwed");

        map.put("A",list);

        System.out.println(map);


        ArrayList<String> list1=new ArrayList<String>();
        list1.add("Ben");
        list1.add("Blun");
        list1.add("Black");
        map.put("B",list1);
        System.out.println(map);

    }
```





#### 9.1.1 Map遍历

```java
 		//1.获取key，通过Key遍历
        Set<String> set = map.keySet();
        for (String s:set){
            ArrayList arrayList = map.get(s);
            System.out.println(s+"=> "+arrayList);
        }

        //2.以键值对实体的方式遍历
        Set<Map.Entry<String, ArrayList>> entries = map.entrySet();
        for (Map.Entry<String,ArrayList> entry:entries){
            System.out.println(entry.getKey()+" = "+entry.getValue());
        }
```

#### 9.1.2 HashMap

 HashMap中的 key 底层数据结构是HashSet(key相同，则会进行内容的比较，不同则更新value。需重写hashcode和equals两个方法)

#### 9.1.3 hashMap 工作原理

当向hashMap中通过Key添加元素时，首先计算hashcode，y=k(x)散列位置，如果该位置没有元素，hashmap执行添加操作。如该位置有元素，则和该链的元素比较，如key相同，执行HashMap更新操作，如key不相同，则执行hashmap添加操作。

#### 9.1.4 LinkedHashMap

LinkedHashMap中的key底层数据结构是LinkedHashSet。key保持添加次序。

#### 9.1.5 TreeMap

TreeMap 中的Key的底层数据结构是TreeSet.

```java
public static void main(String[] args) {

        TreeMap<Studen,String> map =new TreeMap<Studen, String>(new Comparator<Studen>() {
            @Override
            public int compare(Studen o1, Studen o2) {
                return o1.getName().length() - o2.getName().length();
            }
        });

        Studen s1=new Studen("alexx",24,Gender.男);
        Studen s2=new Studen("aple",24,Gender.男);
        Studen s3=new Studen("aaaaaaa",24,Gender.男);

        map.put(s1,"banana");
        map.put(s2,"apple");
        map.put(s3,"coco");

        //修改操作
        Studen s4=new Studen("eeeeeee",24,Gender.男);
        map.put(s4,"COCO");
        System.out.println(map);
    }
```

## 10.1 集合性能的比较



![](..\Collection\imgs\集合性能的比较.png)
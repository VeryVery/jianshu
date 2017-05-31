# Java Set Map List

* 有人想有可以自动扩展的数组,所以有了List  
* 有的人想有没有重复的数组,所以有了set  
* 有人想有自动排序的组数,所以有了TreeSet,TreeList,Tree**  

***因为集合是对数组做的封装,所以,数组永远比任何一个集合要快***

### java.util.List（列表）

* 元素有放入顺序，元素可重复
* 动态增长，查找元素效率高，插入删除元素效率低
* LinkedList（链表结构）
    * LinkedList可被用作堆栈（stack）
    * 随机访问get和set（优先）
* ArrayList（动态数组）
    * 如果要增加的数据量很大，应该使用ensureCapacity()方法，预先设置Arraylist的大小，提高速度
    * 如：ArrayList list = new ArrayList()；list.ensureCapacity(1000)
    * 新增和删除操作（优先）
    * 内存不够时，默认是扩展50% + 1个，
* Vector
    * 线性安全（某一时刻只有一个线程能够写Vector，开销大），效率很低，一般不赞成使用
    * 可以自己限制线性安全，如List list = Collections.synchronizedList(new ArrayList());
    * 内存不够时，默认扩展1倍
    

### java.util.Set（集）
* 元素无放入顺序，元素不可重复，重复元素会覆盖掉
* 查找元素效率低下，删除和插入效率高
* HashSet
    * HashSet获取元素，效率非常高（以空间换时间） 
    * hashcode和equals 判断是否是同一个对象
    * 无序
* TreeSet
    *  会自动排序
    *  存放的对象不能排序则会报错，并且重写comparaTo()方法
* LinkedHashSet
    * LinkedHashSet按照插入顺序保存对象，同时还保存了HashSet的查询速度


### java.util.Map（映射）
* 它有四个实现类,分别是HashMap Hashtable LinkedHashMap 和TreeMap
    *  HashMap
        * 非线程安全,访问速度，遍历，删除，***（无序）***
        * “链表散列”的数据结构,属性中定义了Entry类型的数组
        * 每个 Entry元素其实就是一个key-value对，并且它持有一个指向下一个 Entry元素的引用
        * put:先根据key的重新计算元素的hashCode,根据hashCode得到这个元素在table数组中的位置（即下标），如果数组该位置上已经存放有其他元素了，那么在这个位置上的元素将以链表的形式存放，新加入的放在链头，最先加入的放在链尾。如果数组该位置上没有元素，就直接将该元素放到此数组中的该位置上。
        * HashMap继承AbstractMap
    *  LinkedHashMap
        * HashMap的子类，保存了记录的插入顺序，可以**插入顺序**输出
        * 同时还保存了HashSet的查询速度
    *  TreeMap
        * 实现SortMap接口， 可以**自定义排序**
        * TreeMap继承自SortedMap
    
    * Hashtable
        * 线程安全
        * 但Java 5 提供了ConcurrentHashMap，它是HashTable的替代，比HashTable的扩展性更好
        * hashtable锁住整个Map, ConcurrentHashMap锁的方式是稍微细粒度
    * 我们能否让HashMap同步？
        * HashMap可以通过下面的语句进行同步：
        * Map m = Collections.synchronizeMap(hashMap);




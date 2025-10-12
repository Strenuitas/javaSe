```java
    //匿名内部类写法
    Integer[] arr = {2,3,4,5,112,1,0,3,7,1};

        Arrays.sort(arr, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2 - o1;
            }
        });
    //lambda简化匿名内部类写法
    Integer[] arr = {2,3,4,5,112,1,0,3,7,1};

        Arrays.sort(arr, (Integer o1, Integer o2) -> {
                return o2 - o1;
            }
        );



    public static <T> void sort(T[] a, Comparator<? super T> c) {
        if (c == null) {
            sort(a);
        } else {
            if (LegacyMergeSort.userRequested)
                legacyMergeSort(a, c);
            else
                TimSort.sort(a, 0, a.length, c, null, 0, 0);
        }
    }
    该匿名内部类继承了Comparator的compare方法， Arrays工具类的sort方法前者是要排序的数组，后面就可以是排序的规则， 这是它的TimSort方法决定的，
    后面排序规则若 返回值正数，前者也就是o1排后面，返回值负数，前者o1排后面，即return o1 - o2;按照升序排列，return o2 - o1 按照降序排列。
    这个Comparator类里面的唯一抽象方法就是compare，所以jvm能够识别lambda写法，jvm会将他转换成对应的匿名内部类的写法，也就是最上面的那种写法
```
# 接口里的方法默认就是抽象的.

唯一抽象方法排除1：继承自Object类的方法，2.default方法，是java8引入的特性，允许接口提供"默认实现"，不算做抽象方法 3.static方法，类似工具方法，不属于抽象方法

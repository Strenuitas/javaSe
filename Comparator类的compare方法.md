```java
    Integer[] arr = {2,3,4,5,112,1,0,3,7,1};

        Arrays.sort(arr, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2 - o1;
            }
        });
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

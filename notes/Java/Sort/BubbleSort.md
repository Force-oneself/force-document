# 排序算法---冒泡排序

​	经典算法实现

``` java
public Integer[] sort(Integer[] array) {
    for (int i = 0, size = array.length; i < size - 1; ++i) {
        for (int j = 0; j < size - 1 - i; ++j) {
            // 降序
            if (array[j] - array[j + 1] < 0) {
                // 交换位置
                T temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }
    return array;
}
```

​	在上面我们可以明显的看到两次遍历数组，如果说数组已经有序了，那么后面遍历的就是多余的，因此我们需要提前的判断数组是否有序了，接着尽早返回有序数组提高效率。

``` java
public Integer[] sort(Integer[] array) {
    for (int i = 0, size = array.length; i < size - 1; ++i) {
        // 标识当前遍历是否发生位置交换
        boolean swapped = false;
        for (int j = 0; j < size - 1 - i; ++j) {
            // 降序
            if (array[j] - array[j + 1] < 0) {
                // 交换位置
                T temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
                // 位置交换设置为true
                swapped = true;
            }
        }
        // 如果在遍历中没有发生交换位置，即说明数组已经有序，退出遍历返回
        if (!swapped) {
            break;
        }
    }
    return array;
}
```

​	通过内循环有无发生位置交换来判断数组是否有序，进而冒泡排序的效率便提高了。那么问题来了，如果我需要一个Long数组的排序呢，是不是Ctrl+C 加Ctrl+V呢？这是我们就需要升级下算法。

``` java
// 通过接口来标识该数组是可排序的
public <T extends Comparable<T>> T[] sort(T[] array) {
    for (int i = 0, size = array.length; i < size - 1; ++i) {
        // 标识当前遍历是否发生位置交换
        boolean swapped = false;
        for (int j = 0; j < size - 1 - i; ++j) {
            // 降序
            // 通过接口方法实现，可以定制自己的需求
            if (array[j].compareTo(array[j + 1]) < 0) {
                // 交换位置
                T temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
                // 位置交换设置为true
                swapped = true;
            }
        }
        // 如果在遍历中没有发生交换位置，即说明数组已经有序，退出遍历返回
        if (!swapped) {
            break;
        }
    }
    return array;
}
```


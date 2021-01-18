# 1. Two Sum

## 题目

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## 题目大意

在数组中找到 2 个数之和等于给定值的数字，结果返回 2 个数字在数组中的下标。

## 解题思路

梦开始的地方~

这道题最优的做法时间复杂度是 O(n)。

方法一：双重for循环的暴力枚举

方法二：哈希表

```java
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> hashtable = new HashMap<Integer, Integer>();
    for (int i = 0; i < nums.length; i++) {
        if (hashtable.containsKey(target - nums[i])){
            return new int[]{hashtable.get(target - nums[i]), i};
        }
        hashtable.put(nums[i], i);
    }
    return new  int[0];
}
```

没有满足条件时候的for循环做的事情，其实只是为了put进数据，键为nums[i]（数组元素）， 值为i（数组下标）。

直到有一次的if通过containKey方法找到了满足条件的键，然后就返回这个键对应的值（也就是数组下标）以及当前循环到的i

## 知识点

Java 类库为映射提供了两个通用的实现：HashMap 和 TreeMap。这两个类都实现了 Map 接口。

散列或比较函数**只能作用于键**。与键关联的值不能进行散列或比较。
与集一样，散列稍微快一些，如果不需要按照排列顺序访问键，就最好选择散列。

每当往映射中添加对象时，必须同时提供一个键。
要想检索一个对象，必须使用（因而，必须记住）一个键。

键必须是唯一的。不能对同一个键存放两个值。

- V get(Object key)
  获取与键对应的值；返回与键对应的对象， 如果在映射中没有这个对象则返回 null。
  键可以为 null。
- boolean containsKey(Object key)
  如果在映射中已经有这个键， 返回 true。
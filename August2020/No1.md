### leetcode1:

#### [1. 两数之和](https://leetcode-cn.com/problems/two-sum/)

![image-20200822210437548](http://akatsuke.com/image-20200822210437548.png)

这个题的解法，

1. 首先是暴力枚举的方式进行求解，双重for循环，暴力求出解（这个解法的时间复杂度为O(n²)， 空间复杂度O(1)）：

   ```go
   //golang的写法：
   func twoSum(nums []int, target int) []int {
       length := len(nums)
       for i := 0; i < length - 1; i ++ {
           for j := i + 1; j < length; j ++ {
               if(nums[i] + num[j] == target){
                   return []int{i, j}
               }
           }
       }
       return nil
   }
   ```

   ```java
   //java写法
   public int[] twoSum(int[] nums, int target) {
       int len = nums.length;
       for (int i = 0; i < len - 1; i ++) {
           for (int j = i + 1; j < len; j ++) {
               if(nums[i] + nums[j] == target){
                   return new int[]{i, j};
               }
           }
       }
       return null;
   }
   ```

   

2. 可以使用hash表的方式来进行求解，在遍历数组的第i个值的时候，先查询map中是否存在target - num[i],如果存在就饭回下标组成的数组，如果为查询到则将数组的的值放到map中，这个方法只用便利数组一次，所以这个方法啊时间复杂度O(n)，因为创建了一个map，所以空间复杂度为O(N)：

   ```go
   //golang的写法
   func twoSum(nums []int, target int) []int {
       m := make(map[int]int)
       for k, v := range nums {
           if _, ok := m[target - v]; ok {
               return []int{k, m[target - v]}
           }
           m[v] =k
       }
       return nil
   }
   ```

   ```java
      public int[] twoSum(int[] nums, int target) {
          HashMap<Integer, Integer> map = new HashMap<>();//map的key存数组的值，value存数组的索引值
          for(int i = 0; i < nums.length; i ++) {
              if(map.containsKey(target - nums[i])){  //因为map的key是数组的值，所以判断该key是否存在map中
                  return new int[]{i, map.get(target - nums[i])}; 
              }
              map.put(nums[i], i);
          }
          return null;
      }
   ```

   
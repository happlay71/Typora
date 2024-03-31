给你一个 **非负** 整数数组 `nums` 和一个整数 `k` 。

如果一个数组中所有元素的按位或运算 `OR` 的值 **至少** 为 `k` ，那么我们称这个数组是 **特别的** 。

请你返回 `nums` 中 **最短特别非空** 子数组的长度，如果特别子数组不存在，那么返回 `-1` 。

 

**示例 1：**

**输入：**nums = [1,2,3], k = 2

**输出：**1

**解释：**

子数组 `[3]` 的按位 `OR` 值为 `3` ，所以我们返回 `1` 。

**示例 2：**

**输入：**nums = [2,1,8], k = 10

**输出：**3

**解释：**

子数组 `[2,1,8]` 的按位 `OR` 值为 `11` ，所以我们返回 `3` 。

**示例 3：**

**输入：**nums = [1,2], k = 0

**输出：**1

**解释：**

子数组 `[1]` 的按位 `OR` 值为 `1` ，所以我们返回 `1` 。

 

**提示：**

- `1 <= nums.length <= 50`
- `0 <= nums[i] <= 50`
- `0 <= k < 64`

# 解

```python
class Solution:
    def minimumSubarrayLength(self, nums: List[int], k: int) -> int:
        n = len(nums)
        
        for i in range(n):
            for j in range(n - i): 
                l = []
                for p in range(j, j + i + 1):
                    l.append(nums[p])
                count = self.su(l)
                if count >= k: return i + 1
        return -1
    
    def su(self, nums) -> int:
        count = 0
        for i in range(len(nums)):
            count = nums[i] | count
        return count
```

```python
class Solution:
    def minimumSubarrayLength(self, nums: List[int], k: int) -> int:
        n = len(nums)
        
        for i in range(n):
            for j in range(n - i): 
                l = []
                count = 0
                for p in range(j, j + i + 1):
                    # l.append(nums[p])
                    count = nums[p] | count
                # count = self.su(l)
                if count >= k: return i + 1
        return -1
    
    # def su(self, nums) -> int:
    #     count = 0
    #     for i in range(len(nums)):
    #         count = nums[i] | count
    #     return count
```


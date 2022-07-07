# 数组重复元素
> 输入：nums = [1,2,3,1]<br />
> 输出：true
***
## 自己初探（排序法）
### C++
~~~ c++
    bool containsDuplicate(vector<int>& nums) {
        int n = nums.size();
        sort(nums.begin(),nums.end());
        vector<int>::iterator new_nums = unique(nums.begin(),nums.end());
        nums.erase(new_nums,nums.end());
        int n_new = nums.size();
        if (n == n_new) {
            return false;}else{
                return true;} 
    }
~~~
### python
~~~ python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        nums.sort();
        n = len(nums);
        flag = 0;
        for i in range(n-1):
            if (nums[i] == nums[i+1]):
                return True;
        return False;
~~~
### java
~~~ java
import java.util.Arrays;
class Solution {
    public boolean containsDuplicate(int[] nums) {
        int n = nums.length;
        Arrays.sort(nums);
        for (int i = 0;i<n-1;++i){
            if (nums[i] == nums[i+1]){
                return true;
            }
        }
        return false;
    }
}
~~~
### <font size = '4'> <font style="color: green;">复杂度分析</font></font><br />
> <font size='4'>时间复杂度：O(Nlog⁡N)，其中 N 为数组的长度。需要对数组进行排序。<br />
> 空间复杂度：O(log⁡N)，其中 N 为数组的长度。</font>

## 哈希表法
<font size = '4'>方法描述：对于数组中每个元素，我们将它插入到哈希表中。如果插入一个元素时发现该元素已经存在于哈希表中，则说明存在重复的元素。</font><br />
### C++
~~~ c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> s;
        for (int x: nums) {
            if (s.find(x) != s.end()) {
                return true;
            }
            s.insert(x);
        }
        return false;
    }
};
~~~
### java
~~~ java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<Integer>();
        for (int x : nums) {
            if (!set.add(x)) {
                return true;
            }
        }
        return false;
    }
}
~~~
### <font size = '4'> <font style="color: green;">复杂度分析</font></font><br />
> <font size='4'>时间复杂度：O(N)，其中 N 为数组的长度。<br />
> 空间复杂度：O(N)，其中 N 为数组的长度。</font>
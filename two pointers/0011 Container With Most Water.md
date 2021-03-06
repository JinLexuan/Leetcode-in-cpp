# 11. Container With Most Water
https://leetcode-cn.com/problems/container-with-most-water  
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.Notice that you may not slant the container.  

<img width="559" alt="image" src="https://user-images.githubusercontent.com/60777462/152729683-ab2dd9b9-23ef-4bd3-8c95-2b278d0d762c.png">

Example 1:  
Input: height = [1,8,6,2,5,4,8,3,7]  
Output: 49  
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.  

Example 2:
Input: height = [1,1]  
Output: 1  
 

Constraints:  
n == height.length  
2 <= n <= 105  
0 <= height[i] <= 104  

``` cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int left=0,right=height.size()-1,ans=0;
        while(left<right){
            ans=max(ans,(right-left)*min(height[right],height[left]));
            if (height[right]<=height[left]) right--;
            else left++;
        }
        return ans;
    }
};
```

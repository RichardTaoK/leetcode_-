## 更新五个题

### 6.29

- 力扣11：盛水最多的题

  ```python
  #暴力法是直接左指针，有指针从左指针+1开始，直到最后，只是时间通不过
  #双指针法：通过l,r两个指针，同时向里逼近，每次计算最大的面积，向里逼近的那一方是短板哪一方，因为向里的时候长已经变小了，那如果长板向里走，那么面积肯定会小，只有短板向里走面积才会变大
  def maxArea(height):
      maxcontainer=0
      i=0
      j=len(height)-1
      while i<j:
          if height[i]<height[j]:
          maxcontainer=max(maxcontainer,height[i]*(j-i))
          i+=1
      else:
          maxcontainer=max(maxcontainer,height[j]*(j-i))
          j-=1
      return maxcontainer
  
  ```

  ```javascript
  var maxArea = function(height) {
      let i=0;
      let j=height.length-1;
      var maxcontainer=0;
      while(i<j){
          if(height[i]<height[j]){
              maxcontainer=Math.max(maxcontainer,height[i]*(j-i));
              i+=1;
          }else{
              maxcontainer=Math.max(maxcontainer,height[j]*(j-i));
              j-=1;
          }
      }
      return maxcontainer;
      
  };
  ```

- 219 存在重复元素2

  ```python
  #算法思想：暴力法每k个判断一下，但是时间通不过
  #python  hash的方法，因为hash时间是o(1)，遍历数组的时候发现hash里面没有key时，就把其放到hash里，若还没到k长度，就出现重复时，直接return True；若是hash字典的长度达到k时说明这k个是灭有重复的，直接将第一个删掉，但是这个好像很费时间。
  #暂时没有找到好的方法了
  class Solution:
      def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
          if len(nums)==0:return False
          if k==0:return False
          a={}
          for i in range(len(nums)):
              if nums[i] in a.keys():
                  return True
              else:
                  a[nums[i]]=1
              if len(a)>k:
                  del a[nums[i-k]]
          if len(a)>0:
              return False
  
  ```

  
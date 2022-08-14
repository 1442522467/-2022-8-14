## leetcode题目：905按奇偶排序数组
给你一个整数数组  `nums`，将  `nums`  中的的所有偶数元素移动到数组的前面，后跟所有奇数元素。
返回满足此条件的  **任一数组**  作为答案。
```
class Solution {
    public int[] sortArrayByParity(int[] nums) {
        int n = nums.length, index = 0;
        int[] res = new int[n];
        for (int num : nums) {
            if (num % 2 == 0) {
                res[index++] = num;
            }
        }
        for (int num : nums) {
            if (num % 2 == 1) {
                res[index++] = num;
            }
        }
        return res;
    }
}

```
###用归并算法进行解答
```
import java.util.Arrays;

class  Solution {

public  int[] sortArrayByParity(int[] arr)

{

int[] temp=Arrays.copyOf(arr,arr.length);

sort(arr,0,arr.length-1,temp);

return arr;

}

public  void  sort(int[] arr,int  l,int  r,int[] temp)

{

if(l>=r)return;

int  mid=l+(r-l)/2;

sort(arr,l,mid,temp);

sort(arr,mid+1,r,temp);

if(arr[mid+1]%2==0)

{

merge(arr,l,mid,r,temp);

}

}

public  void  merge(int[] arr,int  l,int  mid,int  r,int[] temp)

{

System.arraycopy(arr,l,temp,l,r-l+1);

int  i=l,j=mid+1;

for(int  k=l;k<=r;k++)

{

if(l>mid)

{

arr[k]=temp[j];

j++;

}

else  if(j>r)

{

arr[k]=temp[i];

i++;

}

else  if(temp[i]%2==0)

{

arr[k]=temp[i];

i++;

}

else  if(temp[j]%2==0)

{

arr[k]=temp[j];

j++;

}

else

{

arr[k]=temp[i];

i++;

}

}

}

}
```

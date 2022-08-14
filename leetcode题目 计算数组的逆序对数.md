## leetcode题目：剑指 Offer 51. 数组中的逆序对
在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。
```
class  Solution {

		private  int  res=0;

		public  int  reversePairs(int[] nums) {

		int[] temp=new  int[nums.length];

		res=0;

		sort(nums,0,nums.length-1,temp);

		return res;

		}

		  

		public  void  sort(int[] nums,int  l,int  r,int[] temp)

		{

		if(l>=r)return;

		int  mid=l+(r-l)/2;

		sort(nums,l,mid,temp);

		sort(nums,mid+1,r,temp);

		if(nums[mid]<nums[mid+1])

		{

		merge(nums,l,mid,r,temp);

		}

		}

		public  void  merge(int[] nums,int  l,int  mid,int  r,int[] temp)

		{

		System.arraycopy(nums,l,temp,l,r-l+1);

		int  i=l,j=mid+1;

		for(int  k=l;k<=r;k++)

		{

		if(i>mid)

		{

		nums[k]=temp[j];

		j++;

		}

		else  if(j>r)

		{

		nums[k]=temp[i];

		i++;

		}

		else  if(temp[i]<temp[j])

		{

		nums[k]=temp[i];

		i++;

		}

		else

		{

		res+=mid-i+1;

		nums[k]=temp[j];

		j++;

		}

	}

		}

		}
```

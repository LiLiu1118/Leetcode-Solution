# 常见排序算法原理及实现

![排序算法复杂度](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E6%8E%92%E5%BA%8F%E7%AE%97%E6%B3%95%E5%A4%8D%E6%9D%82%E5%BA%A6.png)

**=========================================================**

### 1.冒泡排序

##### 算法描述:

##### 比较相邻两个数据如果。第一个比第二个大，就交换两个数对每一个相邻的数做同样1的工作，这样从开始一队到结尾一队在最后的数就是最大的数。针对所有元素上面的操作，除了最后一个。重复1~3步骤，直到顺序完成。

![冒泡排序](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E5%86%92%E6%B3%A1%E6%8E%92%E5%BA%8F.gif)

```c++
#include <iostream>
#include <vector>
using namespace std;
int main(int argc, char **argv) {
    int data[] = {9, 1, 4, 3, 20, 17, 19};
    vector<int> nums(data, data+7);
    for (int i=nums.size(); i > 0; i--)
    {
	for (int j=0; j <= i-1; j++)
	{
	    if (nums[j] > nums[j+1])
	    {
		int tmp;
		tmp = nums[j];
		nums[j] = nums[j+1];
		nums[j+1] = tmp;
	    }
	    
	}
    }
    for (int i=0; i < nums.size(); i++)
    {
	cout << nums[i] << endl;
    }    
    return 0;
}
```

### 2.选择排序

##### 算法描述:

##### 在一个长度为 N 的无序数组中，第一次遍历 n-1 个数找到最小的和第一个数交换。第二次从下一个数开始遍历 n-2 个数，找到最小的数和第二个数交换。重复以上操作直到第 n-1 次遍历最小的数和第 n-1 个数交换，排序完成。

![选择排序](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E9%80%89%E6%8B%A9%E6%8E%92%E5%BA%8F.gif)

```c++
#include <iostream>
#include <vector>
using namespace std;
int main(int argc, char **argv) {
    int data[] = {9, 1, 4, 3, 20, 17, 19};
    vector<int> nums(data, data+7);
    for (int i=0; i < nums.size()-1; i++)
    {
	for (int j=i+1; j < nums.size(); j++)
	{
	    if (nums[j] < nums[i])
	    {
		int tmp;
		tmp = nums[i];
		nums[i] = nums[j];
		nums[j] = tmp;
	    }    
	}
    }
    for (int i=0; i < nums.size(); i++)
    {
	cout << nums[i] << endl;
    }    
    return 0;
}
```

### 3.插入排序

##### 算法描述:

##### 从第一个元素开始，该元素可以认为已经被排序；取出下一个元素，在已经排序的元素序列中从后向前扫描；如果该元素（已排序）大于新元素，将该元素移到下一位置；重复步骤3，直到找到已排序的元素小于或者等于新元素的位置；将新元素插入到该位置后；重复步骤2~5。

![插入排序](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E6%8F%92%E5%85%A5%E6%8E%92%E5%BA%8F.gif)

```c++
#include <iostream>
#include <vector>
using namespace std;
int main(int argc, char **argv) {
    int data[] = {9, 1, 4, 3, 20, 17, 19};
    vector<int> nums(data, data+7);
    for (int i=1; i < nums.size(); i++)
    {
	int key = nums[i];
	int j = i - 1;
	while (j >= 0 && key < nums[j])
	{
	    nums[j+1] = nums[j];
	    j--;
	}
	nums[j+1] = key;	
    }
    for (int i=0; i < nums.size(); i++)
    {
	cout << nums[i] << endl;
    }    
    return 0;
}
```

### 4.快速排序

##### 算法描述:

##### 快速排序使用分治法来把一个串（list）分为两个子串（sub-lists）。下图为in place版本

https://www.youtube.com/watch?v=htRWn-NMZnc

![快速排序](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F.gif)

##### 下图不是in place版本，更容易理解，需要额外空间是因为用了递归，不用递归在其他地方也会产生额外空间消耗

![快速排序](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F.jpg)

```c++
#include <iostream>
#include <vector>
using namespace std;

vector<int> quicksort(vector<int> &a, int left, int right);
int partition(vector<int> &a, int left, int right);
void swap (vector<int> &a, int i, int j);

int main(int argc, char **argv) {
    int data[] = {9, 1, 4, 3, 20, 17, 19};
    vector<int> nums(data, data+7);
    quicksort(nums, 0, nums.size()-1);     
    for (int i=0; i < nums.size(); i++)
    {
	cout << nums[i] << endl;
    }
    return 0;
}

vector<int> quicksort(vector<int> &a, int left, int right)
{
    int partitionindex;
    if (left < right)
    {
	partitionindex = partition(a, left, right);
	quicksort(a, left, partitionindex-1);
	quicksort(a, partitionindex+1, right);
    }
    return a;
}

int partition(vector<int> &a, int left, int right)
{
    int pivot = left, index = pivot + 1;
    for (int i=index; i <= right; i++)
    {
	if (a[i] < a[pivot])
	{
	    swap(a, i, index);   
	    index++;
	    //右边存放较大的部分,indx表示右边最靠内侧的下标
	}
    }
    swap(a, pivot, index-1);
    return index-1;
}

void swap (vector<int> &a, int i, int j)
{
    int tmp = a[i];
    a[i] = a[j];
    a[j] = tmp;
}
```

### 5.归并排序

![归并排序](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E5%BD%92%E5%B9%B6%E6%8E%92%E5%BA%8F.jpg)


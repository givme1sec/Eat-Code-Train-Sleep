## 剑指Offer 66.构建乘积数组

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) `easy`

给定一个数组 `A[0,1,...,n-1]` ，请构建一个数组 `B[0,1,...,n-1]` ，其中 `B` 中的元素 `B[i]=A[0]×A[1]×...×A[i-1]×A[i+1]×...×A[n-1]` 。不能使用除法。<br><br>
**示例：**<br>
```
输入：[1,2,3,4,5]
输出：[120,60,40,30,24]
```
**提示：**<br>
* 所有元素乘积之和不会溢出32位整数
* `a.length <= 100000`

## Submit `C++`
```cpp
class Solution{
public:
    vector<int> constructArr(vector<int>& a){
        int n = a.size();
        vector<int> b(n,1);
        int left = 1;
        int right = 1;
        // left用于保存左侧累乘的值
        // right用于保存右侧累乘的值
        
        // 乘积数组b[i]的值分成两步来求，i左侧累乘和i右侧累乘
        
        // 得到左侧累乘的结果
        for(int i=0;i<n;i++){
            b[i] = left;
            left = left * a[i];
        }
        // 将左侧累乘的结果与右侧累乘相乘
        for(int j=n-1;j>=0;j--){
            b[j] = b[j] * right;
            right = right* a[j];
        }
        return b;
    }
};
```

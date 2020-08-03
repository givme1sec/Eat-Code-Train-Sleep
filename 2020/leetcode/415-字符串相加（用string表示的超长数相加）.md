## 415.字符串相加

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) `easy`

给定两个字符串形式的非负整数 `num1` 和 `num2` ，计算它们的和。<br><br>
**注意：**<br>
* `num1` 和 `num2` 的长度都小于5100.
* `num1` 和 `num2` 都只包含数字 `0-9`.
* `num1` 和 `num2` 都不包含任何前导零.
* **你不能使用任何内建BigInteger库，也不能直接将输入的字符串转换为整数形式.**

## Submit `C++`
```cpp
// 字符串加法、链表加法以及二进制加法等都可以用这种方法

class Solution{
public:
    string addStrings(string num1, string num2){
        // cur用来保存进位，ans用来保存结果
        int cur = 0, i = num1.size()-1, j = num2.size()-1;
        string ans;
        while(i>=0 || j>=0 || cur!=0){
        // 将char型'0'~'9'转换成int型，使用int(char-'0')的方法得到int值，而不能直接使用int(char)，结果会
        // 不一样，如int('9'+'9')得到114，而int(('9'-'0')+('9'-'0'))得到18
        
            if(i>=0) cur += num1[i--] - '0'; 
            if(j>=0) cur += num2[j--] - '0';
        // cur%10，如cur=9+9=18时，取模10得到低位8，加入ans中，cur/10得到进位为1，继续参与下一步运算
            ans += to_string(cur%10);
            cur /= 10;
        }
        
        // 由于低位是从前往后加入ans的，将ans反转得到最终的结果string
        reverse(ans.begin(), ans.end());
        return ans;
    }
};
```

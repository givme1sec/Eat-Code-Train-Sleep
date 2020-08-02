## 剑指Offer 58.翻转单词顺序

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) `easy`

输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。<br>
为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"。<br>

**示例1：**<br>
```
输入："the sky is blue"
输出："blue is sky the"
```
**示例2：**<br>
```
输入："  hello world!"
输出："world! hello"
解释：输入字符串可以在前面或后面包含多余的空格，但是反转后的字符不能包括
```
**示例3：**<br>
```
输入："a good   example"
输出："example good a"
解释：如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。
```

## Submit `C++`
```cpp
class Solution{
public:
    string reverseWords(string s){
    
        // 反转操作首先想到栈，因为栈是先进后出的结构
        stack<string> stk;
        string ans, str;
        
        // istringstream函数的作用是，从string对象中读取用空格或换行符分隔的字符
        // 如"  hello    world!"使用istringstream读取后得到"hello"和"world!"，消除了字符串前后和中间的空格分隔符
        istringstream ss(s);
        
        while(ss >> str){
            stk.push(str);
            stk.push(" ");
            // 每进栈一个单词，同时进栈一个空格分隔符
        }
        if(!stk.empty()){
            // 最后一个单词后的空格分隔符是多余的，需要去掉
            stk.pop();
        }
        while(!stk.empty()){
            // 使用top得到栈顶元素，拼接后再出栈，使用top()可以返回栈顶，而pop()函数无返回值
            ans = ans + stk.top();
            stk.pop();
        }
        return ans;
    }
};
```

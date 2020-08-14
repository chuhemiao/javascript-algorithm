### 1047. 删除字符串中的所有相邻重复项

### 题目描述


+ 给出由小写字母组成的字符串 S，重复项删除操作会选择两个相邻且相同的字母，并删除它们。

+ 在 S 上反复执行重复项删除操作，直到无法继续删除。

+ 在完成所有重复项删除操作后返回最终的字符串。答案保证唯一。

### 示例

+ 输入："abbaca"
+ 输出："ca"
+ 解释：例如，在 "abbaca" 中，我们可以删除 "bb" 由于两字母相邻且相同，这是此时唯一可以执行删除操作的重复项。之后我们得到字符串 "aaca"，其中又只有 "aa" 可以执行重复项删除操作，所以最后的字符串为 "ca"。

### Notice

+ 1 <= S.length <= 20000
+ S 仅由小写英文字母组成。

### 代码


```

// 正规字符串分割 然后比较上一个和下一个字符串是否相等，循环用splice取最新无重复的新数组
var removeDuplicates = function(S) {
    const len = S.length;
    if (len <= 1) {
        return S;
    }
    const arr = S.split('');
    let index = 0,
        i = 0,
        j = 1;

    while (index < arr.length - 1) {
        if (arr[index] === arr[index + 1]) {
            arr.splice(index, 2); // 取到数组index，删除2位，返回新数组，继续循环
            index = Math.max(index - 1, 0); // 返回index-1 
        } else {
            index++;
        }
    }
    return arr.join(''); // 连接字符串
};

// 正则

var removeDuplicates = function(S) {
    for(var i=0; i<S.length; i++){
        reg = new RegExp(`${S[i]}{2}`)
        while(S.match(reg)){
            S = S.replace(reg, '')
            i = 0
        }
    }
    return S
};

// 递归+正则

var removeDuplicates = function f(S) {
    if(!/([a-z])\1/.test(S)) return S
    return f(S.replace(/([a-z])\1/,''))
};


```



### Leetcode原题地址

+[1047. 删除字符串中的所有相邻重复项](https://leetcode-cn.com/problems/remove-all-adjacent-duplicates-in-string/)
+[MDN splice用法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
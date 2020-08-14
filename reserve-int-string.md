# 字符串、整数--反转相关题


### 前序

+ split()方法将一个字符串对象的每个字符拆出来，并且将每个字符串当成数组的每个元素
+ reverse()方法用来改变数组，将数组中的元素倒个序排列，第一个数组元素成为最后一个，最后一个变成第一个
+ join()方法将数组中的所有元素边接成一个字符串
+ charAt() 方法从一个字符串中返回指定的字符。没有提供索引，charAt() 将使用0


### 反转正整数

+ 思路，转数组，直接使用reverse函数，在连接反转
+ 按不同位数（十分位、百分位、千分位等）取余颠倒返回当前值
+ 字符串拼接，在返回

### 示例

+ 给出一个三位整数，返回这个反转之后三位数。
+ 123 反转之后是 321。 900 反转之后是 9。

```
// 反转连接 适用三位以上的正整数
const reserveInt = function(num) {
    return parseInt([...num.toString()].reverse().join(''));
}

console.log(reserveInt(1012)) // 2101 

// 转数组 在拼接  只能三位以下

const reserveInt = function(num){
    let str = num.toString();
    // charAt() 方法从一个字符串中返回指定的字符。没有提供索引，charAt() 将使用0
    return parseInt(str.charAt(2)+str.charAt(1)+str.charAt());
}

console.log(reserveInt(902)) // 209

```


### 反转整数，可适用上面的三位或多位

+ 考虑正负问题
+ 考虑数字溢出问题

### 示例

+ 给定 x = 123，返回 321

+ 给定 x = -123，返回 -321

+ 给定 x = 1534236469， 返回 0

```

const reserveInt = n => {
  if (n < 0) {
    n = n.toString().split('-')[1]; // 负数提取数字
    n = '-' + [...n].reverse().join('');
    n = +n; // 转数字
  } else {
    n = n.toString(); // 转字符
    n = +[...n].reverse().join(''); // 转为数组 颠倒数组 再合字符 最后转数字
  }
  // 2147483647  -2147483647
  if (n >= Math.pow(2, 31) - 1 || n <= Math.pow(-2, 31) + 1) {
    // 判断溢出
    return 0;
  }
  return n;
};

console.log(reserveInt(209)) // 902
console.log(reserveInt(-1902)) // -2091



```


### 反转字符串



+ 分割，反转，连接
+ 字符串长度，然后拼接

```

// 内置函数

function reverseString(str) { 
    return str.split("").reverse().join(""); 
}



// 字符串拼接

const reserveStr = s => {
  var o = '';
  for (var i = s.length - 1; i >= 0; i--)
    o += s[i];
  return o;
}



// 字符串长度，倒序插入新数组 然后连接字符串
const reserveStr = s => {
  var o = [];
  for (var i = 0, len = s.length; i <= len; i++){
    o.push(s.charAt(len - i));
  }
  return o.join('');
}

// 数组中字符串反转

示例：

+ 输入：["h","e","l","l","o"]
+ 输出：["o","l","l","e","h"]

var reverseString = function(s) {
    let left = 0;
    let right = s.length - 1;
    while (left < right) {
        [s[left], s[right]] = [s[right], s[left]];
        left++;
        right--;
    }
    return s
};

// 

```


### 反转链表 

//todo
# 查找斐波纳契数列中第 N 个数


### 概念

+ 斐波纳契数列，又译为菲波拿契数列、菲波那西数列、斐氏数列、黄金分割数列。


### 数学上表达

+ 以递归的方法来定义，即
  $$F_{0}=0$$ 
  $$F_{1}=1$$ 
  $$F_{n}=F_{n-1}+F_{n-2} (n≧2)$$  
 
+ 简单的说斐波那契数列由0和1开始，之后的斐波那契数就是由之前的两数相加而得出。


### 示例

+  斐波纳契数列的前 10 个数字是：0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...

+ 输入1，输出0
+ 输入2，输出1
+ 输入10，输出34

### 代码

```


// 优化的递归

const fibonacci = n => {
  if (!(typeof n === 'number' && n % 1 === 0 && n > 1)) {
    throw '请输入大于0的整数数字';
  }
  var array = [0, 0, 1];
  let temp = n => {
    if (n == 1 || n == 2) return array[n];
    array[n] = temp(n - 1) + temp(n - 2); // 递归获取推算数组每一个元素的值
    return array[n];
  };
  let num = temp(n);
  array.splice(2, 1); // 将数组恢复成 斐波纳契数列
  return num;
};

// 遍历保存结果

const fibonacci = n => {
  let a = 0,
    b = 1,
    c,
    d = [0];
  for (let i = 1; i < n; i++) {
    c = a + b;
    a = b;
    b = c;
    d.push(a); // 加戏 恢复数列
  }
  console.log(d, '斐波纳契数列');
  return a;
};

// 循环赋值

const fibonacci = n =>  {
  let a = 0, b = 1, c = 0
  if (--n > 1) {
    while (--n) {
      c = a + b
      a = b
      b = c
    }
  } else if (n > 0) {
    c = 1
  }
  return c
}


// 推导法

const fibonacci = n => {
  let num = new Array(n).fill(0); // 初始化数组，并设置初始值
  num[1] = 1; // 设置第二个元素的值 推导第3个元素
  for (let i = 2; i <= n - 1; i++) {
    num[i] = num[i - 2] + num[i - 1]; // 遍历逐步推导元素值 数组完全符合数列不用进行判断等 运行效率最高。
  }
  return num[n - 1]; // 数组是从0开始计算 所以要减1
};


```
# 数组中元素重复相关问题

### 1.1 数组去重并统计重复元素出现的次数实例


### 题目描述

+ 给定一个字符串数组, 计算出当前数组中每个元素出现的次数

### 事例

+ 给定一个数组 var arr = [1, 2, 3, 1, 2, 4];
+ 输出 

```
1,2;
2,2;
3,1;
4,1;

```

### 分析

+ 分别计算数组中每个元素出现的次数，并按指定格式输出

### 代码 (使用set进行数组去重)

```
    var arr = [1,2,3,1,2,4,5,1,2,3,4,7,8];

    function arrayCountEle(arr) {
        var newArr = [];
        newArr = [...new Set(arr)];

        var newarr2 = new Array(newArr.length);

        for(var t = 0; t < newarr2.length; t++) {
            newarr2[t] = 0;
        }

        for(var p = 0; p < newArr.length; p++) {
            for(var j = 0; j < arr.length; j++) {
                if(newArr[p] == arr[j]) {
                    newarr2[p]++;
                }
            }
        }

        for(var m = 0; m < newArr.length; m++) {
            console.log(newArr[m] + "," + newarr2[m]+';');
        }

    }
    // 调用
    arrayCountEle(arr);

```


### 1.1 找出数组中重复最多的元素


### 题目描述

+ 给定一个字符串数组, 每一个元素代表一个 IP 地址，找到出现频率最高的 IP。（频率最高的只有一个）

### 例子

+ 给定一个数组 `arr = ['192.168.0.1','192.168.2.1','192.168.3.1','192.168.0.1'] `

+ 输出 `192.168.0.1`


### 分析

+ 找出数组中重复最多的元素，并输出结果

### 代码

```

let arr =[2,3,3,3,1,2,4,65,6,7,8,8,4,3,3,2,5,7,66] ;

let arr =['192.168.0.1','192.168.2.1','192.168.3.1','192.168.0.1'] 

function my_function(ipLines) {
  
  // 给出默认值
  var [obj, max, name] = [{}, 1, ''];
  ipLines.forEach(value => {
    if (obj[value]) {
      // 已经有值了 就把值+1
      obj[value]++;
      if (obj[value] > max) { // 判断重复次数有没有超过当前最高的
        max = obj[value]; // 重复次数
        name = value; // 当前元素
      }
    } else {
      // 没有值 就初始化一个值
      obj[value] = 1;
    }
  });
  //console.log(name)
  return name;
};

const ele = my_function(arr)
console.log('当前最多的元素是：',ele)

```


### 知识拓展

+ [JavaScript 算法之复杂度分析](https://juejin.im/post/6844903750985842695)
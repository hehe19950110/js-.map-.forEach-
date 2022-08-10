js 合并数组：

题目：

```
[
    {
        code: 1,
        data: [
            { title: 'haha', size: 123 },
            { title: 'xixi', size: 456 }
        ]
    },
    {
        code: 2,
        data: [
            { title: 'cscs', size: 4344 },
            { title: 'vvv', size: 555 }
        ]
    }
]
```
达到：

```
[
  { code: 1, title: 'haha', size: 123 },
  { code: 1, title: 'xixi', size: 456 },
  { code: 2, title: 'cscs', size: 4344 },
  { code: 2, title: 'vvv', size: 555 }
]
```

合并方法一：

```

const result = data.reduce((acc, cur) => 
  acc.concat(
    cur.data.map((item)=> ({
      ...item,
      code:cur.code,
    })
    )
  )
    , [])
```

合并方法二：

```
data.map(item => 
         item.data.map(v =>
                      ({code: item.code, ...v})
         )
        ).flat()
 ```
  
  

数组的方法:  
  
### 1 .map() 

返回一个新数组，数组中的元素为按照原始数组元素顺序依次调用处理后的值。 
 
```
var arr=[3,5,7,9,1,2,4];
var arr1=arr.map(function(item,index,arr){
  return item+10;   //此时数组中的每个元素都加10
});
 =>  arr1=[13,15,17,19,11,12,14];
```
注意：

map不会对空数组进行检测 ；map不会改变原始数组 

### 2 .flat() 

用于将嵌套的数组“拉平”，返回一个新数组，对原数据没有影响。

```
A. [1, 2, [3, 4]].flat()

//  => [1, 2, 3, 4]   原数组的成员里面有一个数组，flat()方法将子数组的成员取出来，添加在原来的位置。

B. [1, 2, [3, [4, 5]]].flat(2)

//  => [1, 2, 3, 4, 5]  flat()的参数为2，表示要拉平两层的嵌套数组。

C. [1, [2, [3]]].flat(Infinity)  
//  => [1, 2, 3]   如果不管有多少层嵌套，都要转成一维数组，可以用Infinity关键字作为参数。
```

### 3 .reduce()

对累计器和数组中的每个元素（从左到右）应用一个函数，将其简化到 单个值。

```
var sum=arr.reduce(function(value,item){
return value+item;
},100);   //函数后面的参数100就是累加的初始值。
```

### 4 forEach用于遍历数组

数组.forEach(function(数组中的元素，每个元素对应的下标，数组自身){ });

注意：forEach可以跳过空元素，forEach没有返回值,使用return无效。

### 5 `Array.isArray();`

判断元素是否是数组，如果是数组返回true，否则返回false。

6 push(); 在数组尾部添加一个或者多个元素，并且返回数组的新长度。

7 pop(); 删除数组尾部的最后一个元素，并且将这个被删除后的新数组返回。

8 concat(); 合并两个或更多的数组，并返回新数组。

```
var arr=[1,2,3,4];
var arr1=[5,6,7,8];
var arr2=arr.concat(arr1);   // => arr2=[1,2,3,4,5,6,7,8];
```

9 join(); 将数组的每个元素以指定的字符连接，形成新字符串返回。

```
var arr=[1,2,3,4,5];
var str=arr.join("|");
 => str=1|2|3|4|5;
```

10 splice() 插入，删除，替换元素。

```
var arr=[1,2,3,4,5];
var arr1=arr.splice(2,2,10,11);
 => arr1=[1,2,10,11,5];  // arr.splice(从什么位置开始,删除多少个元素,要插入的元素);
```

11 indexOf 从前向后查找: .indexOf(要查询的元素,从什么位置下标开始查询)；如果查找到，返回该元素所在的下标，如果没有查找到，则返回-1。

```
var arr=[1,3,1,2,3,5,2,3,4,6];
var index=arr.indexOf(3,2);  //要查询元素3，从下标2开始查询
console.log(index);   //查询到的结果是下标4

var index=arr.indexOf(7); //查找元素7
console.log(index);  //没有查找到返回-1
```

12 sort(); 对数组的元素进行排序（仅适用于数值)。

```
var arr=[0,1,7,2,5,8,10,4,3,6,9];
arr.sort(function(a,b){
  return a-b;  // 后项-前项 从小到大排序;前项-后项 从大到小排序
});
console.log(arr);
 => arr=[0,1,2,3,4,5,6,7,8,9,10];
```

13  filter(); 创建一个新数组, 筛选数组中满足条件的结果.

```
var arr=[1,2,5,7,8,2,4,9,10];
var arr1=arr.filter(function(item,index,arr){
  return item>5;  //将数组中大于5的返回到一个新数组。
});
console.log(arr1);
=> arr1=[5,7,8,9,10];
```

# 向量

## 创建向量
`c()`
`v = c(1,2,3,4,5)`

在R 中会自动转换 向量的值类型
如果全部是 int 则是int
如果一个位string 则 string
可以用NA 标记空值
```
> k = c(T,F,NA,TRUE)
> k
[1]  TRUE FALSE    NA  TRUE
```

创建空向量 `vector()`

```
> x = vector()
> x
logical(0)
> x[5]=5
> x
[1] NA NA NA NA  5
```


## 索引
使用 `向量名称[index]` 来访问向量对应索引的值 索引是从1开始.

可以使用`length(向量名)`来显示向量的长度

## 向量化
R语言中可以使用 函数【函数向量化】 可以直接对每个向量进行操作
```
> v = c(4,7,23.5,80,99)
> x = sqrt(v)
> x
[1] 2.000000 2.645751 4.847680 8.944272 9.949874
```
### 平方根
`sqrt()`
###  加法
```
v1 = c(1,2,3,4,5)
v2 = c(11,22,33,44)
v1 + v2

> v1 = c(1,2,3,4,5)
> v2 = c(11,22,33,44)
> v1 + v2
[1] 12 24 36 48 16
Warning message:
In v1 + v2 :
  longer object length is not a multiple of shorter object length
```
可以看出在长度不相等的情况下
会先使用 短的哪个向量进行循环 在和 另一个向量相加 同时抛出警告
```
v1 = c(1,2,3,4)
v2 = c(10,11)
v1 + v2

> v1 = c(1,2,3,4)
> v2 = c(10,11)
> v1 + v2
[1] 11 13 13 15
```
### 乘法
```
v1 * 2
> v1
[1] 1 2 3 4
> v1 * 2
[1] 2 4 6 8
```
实际上是  v1 * c(2)

## 因子
使用`factor()`转换

```
g = c('f','m','m','m','f','f')
g = factor(g)
g

> g = c('f','m','m','m','f','f')
> g = factor(g)
> g
[1] f m m m f f
Levels: f m
```
上述有2个因子 `f` 和 `m`

手动指定因子
```
g1 = c('m','m','m','m','m')
g1 = factor(g1)
g1
> g1 = c('m','m','m','m','m')
> g1 = factor(g1)
> g1
[1] m m m m m
Levels: m
```
手动指定

```
g1 = c('m','m','m','m','m')
g1 = factor(g1,levels = c('f','m'))
g1

> g1 = c('m','m','m','m','m')
> g1 = factor(g1,levels = c('f','m'))
> g1
[1] m m m m m
Levels: f m
```
### 因子的作用
1. 计算次数
```
> table(g1)
g1
f m
0 5
> table(g)
g
f m
```
2. 计算频率
prop.table(交叉表,维度[1,2])

## 生成序列
`:` 可以快速生成向量
如：
```
1:100
> 1:100
  [1]   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35  36  37
 [38]  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  71  72  73  74
 [75]  75  76  77  78  79  80  81  82  83  84  85  86  87  88  89  90  91  92  93  94  95  96  97  98  99 100
```
`:`的优先级高于 `-`

`seq()` 生成等差序列
```
> seq(from = 1 , to = 5 , length = 4)
[1] 1.000000 2.333333 3.666667 5.000000

> seq(length = 10 , from = -2 , by = 0.2)
 [1] -2.0 -1.8 -1.6 -1.4 -1.2 -1.0 -0.8 -0.6 -0.4
[10] -0.2
```
`rep` 生成指定长度和值的序列
```

> rep(5,10)
 [1] 5 5 5 5 5 5 5 5 5 5
 > rep ('ww',3)
 [1] "ww" "ww" "ww"
 > rep(1:2,3)
 [1] 1 2 1 2 1 2
 > rep(1:2,each = 3)
 [1] 1 1 1 2 2 2
```

`gl()`生成带有因子的序列
`gl(k,n)`k因子水平个数 n 因子重复个数
```
> gl(3,5)
 [1] 1 1 1 1 1 2 2 2 2 2 3 3 3 3 3
Levels: 1 2 3
> gl(2,5,labels = c('f','m'))
 [1] f f f f f m m m m m
Levels: f m
```
`rt()`
`rnorm()`

## 数据子集
```
x = c (0,1,2,-1,-2)
x > 0

> x = c (0,1,2,-1,-2)
> x > 0
[1] FALSE  TRUE  TRUE FALSE FALSE

x[x>0]

> x[x>0]
[1] 1 2
> x
[1]  0  1  2 -1 -2
> x[ x > 1 | x < -1]
[1]  2 -2
> x[ x > 1 & x < 3]
[1] 2

x[c(1,3)]

> x[c(1,3)]
[1] 0 2
```

### 向量元素命名
```
y = c(1,2,3,4)
names(y) = c('name1','name2','name3','name4')

> y = c(1,2,3,4)
> names(y) = c('name1','name2','name3','name4')
> y
name1 name2 name3 name4
    1     2     3     4
```
也可以使用这些命名去访问 向量中的元素
`y['name1']`
```
> y[1]
name1
    1
> y['name1']
name1
    1
```

快速初始化所有元素
`y[] = 0`
```
> y[] = 0
> y
name1 name2 name3 name4
    0     0     0     0
```
# 矩阵
```
> m = c(45,23,66,77,33,44,56,12,78,23)
> dim(m) = c(2,5)
> m
     [,1] [,2] [,3] [,4] [,5]
[1,]   45   66   33   56   78
[2,]   23   77   44   12   23
```
通过`dim` 可以把向量转换为矩阵
也可以通过`matrix`转换
```
> m = matrix(c(45,23,66,77,33,44,56,12,78,23),2,5)
> m
     [,1] [,2] [,3] [,4] [,5]
[1,]   45   66   33   56   78
[2,]   23   77   44   12   23

> m = matrix(c(45,23,66,77,33,44,56,12,78,23),2,5,byrow = T)
> m
     [,1] [,2] [,3] [,4] [,5]
[1,]   45   23   66   77   33
[2,]   44   56   12   78   23
```
在矩阵中 可以使用 `m[1,2]` 这样的方式来访问元素
```
> m[2,3]
[1] 12
> m[1,]
[1] 45 23 66 77 33
> m[,2]
[1] 23 56
> m[-2,1]
[1] 45
> m[1,c(3,5)]
[1] 66 33
> m[1,-c(3,5)]
[1] 45 23 77
```
使用这样的方式最终获取的是一个向量
```
> m[1,,drop=F]
     [,1] [,2] [,3] [,4] [,5]
[1,]   45   23   66   77   33
```
在加上`drop=F`之后得到的仍然是个矩阵

`cbind` 和 `rbind`可以把2个以上的向量或者矩阵合并
```
cbind(c(22,33),c(11,22))
> cbind(c(22,33),c(11,22))
     [,1] [,2]
[1,]   22   11
[2,]   33   22
m1 = matrix(c(45,23,66,77,33,44,56,12,78,23),2,5,byrow = T)
m2 = matrix(rep(10,20),4,5)
m3 = rbind(m1,m2)

> m1 = matrix(c(45,23,66,77,33,44,56,12,78,23),2,5,byrow = T)
> m2 = matrix(rep(10,20),4,5)
> m3 = rbind(m1,m2)
> m3
     [,1] [,2] [,3] [,4] [,5]
[1,]   45   23   66   77   33
[2,]   44   56   12   78   23
[3,]   10   10   10   10   10
[4,]   10   10   10   10   10
[5,]   10   10   10   10   10
[6,]   10   10   10   10   10
```
## 矩阵中的rename
可以使用`colnames` 和 `rownames` 分别对矩阵的行和列进行命名
```
m = matrix(c(45,23,66,77,33,44,56,12,78,23),2,5,byrow = T)
colnames(m) = c('name1','name2','name3','name4','name5')
rownames(m) = c('rowName1','rowName2')

> m = matrix(c(45,23,66,77,33,44,56,12,78,23),2,5,byrow = T)
> colnames(m) = c('name1','name2','name3','name4','name5')
> rownames(m) = c('rowName1','rowName2')
> m
         name1 name2 name3 name4 name5
rowName1    45    23    66    77    33
rowName2    44    56    12    78    23
```
和向量一样 也可以使用对应的name来访问元素
```
m[,'name1']
> m[,'name1']
rowName1 rowName2
      45       44
> m['rowName1',]
name1 name2 name3 name4 name5
   45    23    66    77    33
m['rowName1','name1']
> m['rowName1','name1']
[1] 45
m['rowName1',,drop=F]
 > m['rowName1',,drop=F]
          name1 name2 name3 name4 name5
 rowName1    45    23    66    77    33
```
# 数组
数组是使用 `array()`来进行创建
```
1维数组
a = array(1:5)
> a = array(1:5)
> a
[1] 1 2 3 4 5
多维数组
a = array(1:25,dim = c(5,5))
> a = array(1:25,dim = c(5,5))
> a
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    6   11   16   21
[2,]    2    7   12   17   22
[3,]    3    8   13   18   23
[4,]    4    9   14   19   24
[5,]    5   10   15   20   25
一次创建多个数组
a = array(1:24,dim = c(4,3,2))
> a = array(1:24,dim = c(4,3,2))
> a
, , 1

     [,1] [,2] [,3]
[1,]    1    5    9
[2,]    2    6   10
[3,]    3    7   11
[4,]    4    8   12

, , 2

     [,1] [,2] [,3]
[1,]   13   17   21
[2,]   14   18   22
[3,]   15   19   23
[4,]   16   20   24
```
和向量以及矩阵一样的方法访问数组
```
a[1,1,1]
> a[1,1,1]
[1] 1
> a[,1,1]
[1] 1 2 3 4
> a[1,,1]
[1] 1 5 9
> a[1,,2]
[1] 13 17 21
> a[1,2,]
[1]  5 17
> a[c(1,3),2,]
     [,1] [,2]
[1,]    5   17
[2,]    7   19
```
## 数组和矩阵的运算
```
m = matrix(c(1:20),4,5)
> m = matrix(c(1:20),4,5)
> m
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20
> m * 3
     [,1] [,2] [,3] [,4] [,5]
[1,]    3   15   27   39   51
[2,]    6   18   30   42   54
[3,]    9   21   33   45   57
[4,]   12   24   36   48   60
> m + 3
     [,1] [,2] [,3] [,4] [,5]
[1,]    4    8   12   16   20
[2,]    5    9   13   17   21
[3,]    6   10   14   18   22
[4,]    7   11   15   19   23
```
# 列表
列表其实是一个不同长度，不同数据类型的一个集合.
```
list = list(id = 123,
            name = 'san',
            marks = c(11,22,33,44,55) )
> list = list(id = 123,
+             name = 'san',
+             marks = c(11,22,33,44,55) )
> list
$id
[1] 123

$name
[1] "san"

$marks
[1] 11 22 33 44 55
```
可以使用 `list[[1]]` 或者是 `list$name` 来访问对应的元素
```
> list$name
[1] "san"
> list[[1]]
[1] 123
```
## 列表的重命名
`names`可以对列表进行重命名
```
names(list) = c('rename1','rename2','rename3')
> names(list) = c('rename1','rename2','rename3')
> list
$rename1
[1] 123

$rename2
[1] "san"

$rename3
[1] 11 22 33 44 55
```
## 列表的扩展
可以通过 `列表名$新增属性 = 元素 ` 来进行对列表的扩展
```
> list$addNewItem = c('a','b')
> list
$rename1
[1] 123

$rename2
[1] "san"

$rename3
[1] 11 22 33 44 55

$addNewItem
[1] "a" "b"
```
也可以用`c()`来合并列表
```
list = list(id = 123,
            name = 'san',
            marks = c(11,22,33,44,55) )
other = list(level = 'SE',
            others = 'N'
            )

> list = list(id = 123,
+             name = 'san',
+             marks = c(11,22,33,44,55) )
> other = list(level = 'SE',
+              others = 'N'
+ )
> c(list,other)
$id
[1] 123

$name
[1] "san"

$marks
[1] 11 22 33 44 55

$level
[1] "SE"

$others
[1] "N"
```
## 列表转换
`unlist()` 来把列表转换为向量
```
unlist(list)
> unlist(list)
    id   name marks1 marks2 marks3 marks4 marks5
 "123"  "san"   "11"   "22"   "33"   "44"   "55"
```

## 数据集
数据集是一个特殊的列表
```
dataSet = data.frame(site = c('A','B','C','D'),
                     season = c('Winter','Summer','Summer','Spring'),
                     PH = c(7.4,6.3,8.6,7.2)
                     )

> dataSet = data.frame(site = c('A','B','C','D'),
+                      season = c('Winter','Summer','Summer','Spring'),
+                      PH = c(7.4,6.3,8.6,7.2)
+ )
> dataSet
 site season  PH
1    A Winter 7.4
2    B Summer 6.3
3    C Summer 8.6
4    D Spring 7.2
```
### 访问
可以使用像向量一样的方法去访问
```
> dataSet[3]
   PH
1 7.4
2 6.3
3 8.6
4 7.2
> dataSet[1,3]
[1] 7.4
> dataSet[1,'PH']
[1] 7.4

> dataSet[dataSet$PH>7,]
  site season  PH
1    A Winter 7.4
3    C Summer 8.6
4    D Spring 7.2
> dataSet[dataSet$site=='A','PH']
[1] 7.4
> dataSet[dataSet$site=='A',c('PH','season')]
   PH season
1 7.4 Winter
```
可以使用 `attach()`来简化查询 而不必使用数据集的名称
```
attach(dataSet)
dataSet[site == 'A']
> dataSet[site == 'A']
  site
1    A
2    B
3    C
4    D
> site
[1] A B C D
Levels: A B C D
> PH
[1] 7.4 6.3 8.6 7.2
```
与之相反的是 `detach()` 禁止访问数据集的列(测试无效？)

`subset()` 不绑定 但是可以在方内使用
```
subset(dataSet,PH>7)
> subset(dataSet,PH>7)
  site season  PH
1    A Winter 7.4
3    C Summer 8.6
4    D Spring 7.2
```
## 增加新列
和向量类似但是需要确保`行数相同`

# 函数
创建函数首先要确定方法是否存在。

# 会话
可以使用
```
source(fileName.r)来执行
load(fileName.r)来加载
save()保存
save.image()保存当前的所有镜像
```

课程：列表推导式

目标：

​		列表推导式的使用

​		推导式扩展：



作用：推导式也被称为生成式，用来创建有规律的列表

使用推导式的好处：简化代码量

推导式格式  

```
变量名  =  [  返回值  for  变量名  in   值列表 ]

变量名  =  [  返回值  for  变量名  in   值列表 if  条件 ]
```



快速体验:   

​       创建存储数字0-10 的列表类型变量List1

```
非推导式创建列表

List1=[]
for x  in  range(11):
	List1.append(x)
print(List1)
++++++++++++++++++++++++++++++++++++++++++

使用推导式创建
List1 = [  x  for x  range(11) ]
print List1

带if 的推导式
List1 = [  x  for x  range(11) if  x %  2  ==  0 ]
print List1

推导式使用扩展：
1 多for 实现列表推导式 

创建如下数据的列表 [(1,0),(1,1),(1,2),(2,0),(2,1),(2,2)]
List1=[]
for i in range(1,3):
	for j in range(3):
		List1.append((i,j))
print(List1)

使用列表推导式创建
List1 = [ (i,j) for i in range(1,3) for j in range(3) ]
print(List1)

使用推导式合并列表快速创建字典
>>> lista=["name","age","gender"]
>>> listb=["plj",21,"girl"]

>>> dirc1={lista[i]:listb[i] for i in range(len(lista))}
>>> dirc1
{'name': 'plj', 'age': 21, 'gender': 'girl'}
 
在字典里 获取指定的数据
>>> woker={"Linux":18000,"java":12000,"php":8000,"python":16000,"aid":7800,"bigData":20000}

>>> num = { k:v for k,v in woker.items() if v < 10000}
>>> num
{'php': 8000, 'aid': 7800}
>>> 


```

​       




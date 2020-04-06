# 有【数据感】的从聚合到解聚
## 3.1 分进合击出报表¶
1. pandas剑法
- 分 groupby
- 迸 count, sum, mean, max, min
- 合 agg
2. 数据科学心法
- 分 split
- 迸 apply
- 合 combine
3. 出报表剑法
- 一EXCEL档多分页法:
    + with pd.ExcelWriter() as writer:
    + with open() as fp:
- rename改名法
    + 先练改columns名称(i.e. 变数名称)
    + (以后)再练改index名称(i.e. 观察名称)
- sort_values 排序法
    + 高阶多索引排序以后细练
    + 今日先比划比划先过
### 有关"/"
1. 代表代码未输完，后面仍有代码。
---
## 3.2 把全数据拆分
### 1. 将对象分成组
- 单独一个变量

*传递给的字符串groupby可以引用列级别或索引级别*
```
df_grouped_01 = df.groupby("X")
```
- 多个变量
```
df_grouped_02 = df.groupby(["X","Y"])
```
### 2. GroupBy对象属性
```
df_grouped_01.groups
```
- *该groups属性是一个dict，其键是计算出的唯一组，而对应的值是属于每个组的轴标签*
- *多个级别时，为元组*
---
## 3.3 进行数据计算
- 算某一项的值
```
df["X"].agg("计算")
```
- 算某一组的值
```
df_grouped_01["X"].agg("sum")
```
---
## 3.4 合流数据设计安排报表
- agg 的几种方式（多指标统计的方法
```
df.groupby(["国家","行业"])["估值（亿人民币）"].agg(sum = "sum",mean = "mean",count = "count")
```
```
df.groupby(["国家","行业"])["估值（亿人民币）"].agg(["sum","mean","max","min"])
```
```
df.groupby(["国家","行业"]).agg({"估值（亿人民币）":["sum","mean","count"]})
```
---
## 3.5 数据感
> 数据之天下，天下之数据，合久必分分久必合，从聚合到解聚的操作感是需要我们能掌握的，让我们来总结一下今天学到的数据感，并标记着今日为"数据感"修练的里程碑
### 3.5.1 pandas 的 类别数据
pandas的类别数据（categorical）可以建，使变数不再只是object




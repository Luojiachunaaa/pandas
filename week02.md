- # pandas处理数据
- 探索，清理和处理数据在Pandas中，数据表称为DataFrame
- 对数据科学家来说:
    + 竖着的列column通常放变数variables
    + 横着的行row通常放观察observations
- 对数据及信息管理人员来说:
    + 表格数据（例如存储在电子表格或数据库中的数据）是很常见的，最主流的数据结构和查询语言是SQL
    + 树状文本数据（例如HTML, XML, JSON数据）是很常见的，HTML/XML最主流的查询语言是xpath
```
框框 = pd.DataFrame ( {
        "变数X": ["观察X1", "观察X2", "观察X3", "观察X4"],
        "变数Y": ["观察Y1", "观察Y2", "观察Y3", "观察Y4"],
        "变数Z": ["观察Z1", "观察Z2", "观察Z3", "观察Z4"],
      } )
```
1. pd.DataFrame 的主流参数是字典
2. 该字典的键keys是由变数构成，相当於表格中一行行的标题
3. 该字典的值values是由观察的列表构成，相当於表格中一行行的数据
4. 表格真的要是表格, 该字典的每个观察的列表数量必需齐一
5.  - loc[] 取 观察, 行 column
    - [""] 取 变数, 列 row
---
- # 读写表格数据
*pandas集成了常用的现成的文件格式或数据源（csv，excel，sql，json，parquet等)*
```
读到csv = pd.read_csv("路径档案名", encoding="utf8")
读到tsv = pd.read_csv("路径档案名", encoding="utf8", sep="\t")
读到excel = pd.read_excel("路径档案名", encoding="utf8", sheet_name="分页名称")
```
---
- # 选择表格子集
>切片 (英文叫slice) 是数据科学家找突破点的重要工具，是她们的数据解剖刀。
- 列子集
```
df.loc()
df.iloc()
df.set_index()
df.head(n)
df.tail(n)
df.nlargest(n, '变量')
df.nsmallest(n, '变量')
df[df.估值（亿人民币）> 10]
```
- 行子集
```
df[['变量X','变量Y','变量Z']]
df[['变量X']]
df['变量X']
```
- 列+行子集
```
df.loc[:,['变量X':'变量Z']]    # 注意中括号里的: 和 ,的使用
df.iloc[:,[1,2,5]]
df.loc[df['变量X']>10, ['变量X','变量Z'] ]
```
---
- # pandas绘图
*以数据框为中心的代码实践，减少以图表类型为开头的编程思维来作图*
```
df.plot()
```
---
- # 从现有列创建创建新列
*创建新列就是变数variables的转换*
```
df['新变量'] = df['变量X'] + df['变量Y']
df['新变量'] = [ 转换(x) for x in df['变量Y'] ]     # 列表推导转换
```
---
- # 计算汇总描述性统计信息
```
df.describe()
df.describe(include=all)
df.count()
df.sum()
df.min()
df.max()
df.mean()
df.median()
df.var()
df.std()
```
---

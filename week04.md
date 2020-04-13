# 新增数据与数据框的处理
## 新变量处理
### 字符串处理
- 读档并查看数据信息
- 获取某列Series的str属性，使用各种字符串处理函数
    + 拆分函数*split* 
    ```
    df["某包含多项的变量"].str.split('、'，expand=True)
    ```
    + 查询是否包含某些字符*contains*
    ```
    df["某包含多项的变量"].str.contains("某字符")
    ```
    + 判断是否为数字*isnumeric*
    ```
    df["某变量"].str.isnumeric()
    ```
    + 数字列无法使用str方法*len*
    ```
    df["某数字列"].str.len()
    ```
- 新增一列
    + 直接赋值
    ```
    df.loc[:,"原列名称1_list"]=df["原列名称1"].str.split('、')
    ```
    + df.assign
    ```
    df.assign(
    原列名称2_list = lambda x : x["原列名称2"].str.split('[、,,]'),
    原列名称3_list = lambda x : x["原列名称3"].str.split('[、,,]')
    ```
    *df.assign方法可以同时添加多个新的列*
---
## 数据框重塑
### 数据透视(stack)
- drop()删除某列，作为准备合并的表格
```
df_待合并 =df_独角兽_创始人_准备.drop('掌门人/创始人', axis=1)
```
- split()拆分列元素
```
df['掌门人/创始人'].str.split(',', expand=True)
```
- stack以最内层为索引堆叠,并删除某列的索引
```
df['掌门人/创始人'].str.split(',', expand=True).stack().reset_index(level=1,drop=True)
```
- Extra 我们给新的Series命名
```
df_准备合并的列 =df['掌门人/创始人'].str.split(',', expand=True).stack().reset_index(level=1,drop=True).rename('掌门人/创始人')
```
---
## 数据框整合
### merge进行合并
1. 数据会被复制
2. 数目以多的一边为准
```
df_独角兽_创始人 = pd.merge(df_待合并,df_准备合并的列,on= "序号")
```








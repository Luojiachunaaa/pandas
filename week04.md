# 新增数据与数据框的处理
## 新变量处理
### 1. 字符串处理
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
)
    ```
    *df.assign方法可以同时添加多个新的列*
---
## 数据框重塑

---
## 数据框整合

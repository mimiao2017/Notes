2_Indexing,slicing
---
读入CSV文件，显示前几行
``` python
data = pd.read_csv()
data.head()
```
获取某个column的所有值
``` pandas
data["description"]
```
获取某个column的第n个值
``` pandas
data["deacription"][0]
```
获取某一行的所有值
``` pandas
data.iloc[0]
```
获取某个column的某几个值
```
data.iloc[0:10,1]
data[1][0:10]
```
取出数据集中的某几行组成新的数据集
```
data.iloc[[1,2,3,5,8]]
```
>

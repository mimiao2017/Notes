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

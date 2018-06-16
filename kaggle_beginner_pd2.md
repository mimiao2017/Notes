PandasLesson2_Indexing,slicing
--------------
读入CSV文件，显示前几行
``` python
data = pd.read_csv()
data.head()
```
获取某个column的所有值
``` pandas
data["description"]
or
data.description
or
data.loc[0:,"description"]
```
获取某个column的第n个值
``` pandas
data["deacription"][0]
or 
data.loc[0,"description"]
```
获取某一行的所有值
``` pandas
data.iloc[0]
```
获取某个column的某几个值
```
data.iloc[0:10,1]
data.loc[0:,'country']
data[1][0:10]
```
取出数据集中的某几行组成新的数据集
```
data.iloc[[1,2,3,5,8]]
```
`注意iloc\loc\ix的区别`
* iloc:通过行号（index）索引
* loc:通过标签('label')索引（比较通用）,
  .loc的使用格式必须是data.loc[n:m,'label'],不能只有行坐标或者列坐标
* ix:通过行号和标签索引(不推荐使用)

取出满足某个条件的所有数据
```
reviews.loc[reviews.country == 'Italy']
or
reviews[reviews.country == 'Italy']
```
取出满足某个条件的数据的某一列/行
```
reviews[revoews.country == 'Italy'].points
or
reviews[revoews.country == 'Italy']['points']
```
取出某一列的最后1000行数据
```
reviews.loc[-1000:, 'Italy']
```
取出同时满足n个要求的行和列
```
reviews.loc[reviews.country.isin(["Italy","France"]) & (reviews.points >= 90)].country
#筛选：产自意大利或者法国的、评分高于90的酒，格式为index+country
```

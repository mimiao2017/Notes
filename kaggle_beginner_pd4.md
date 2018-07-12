# Grouping

**summary中用到的df.value_counts()实际上是指向df.groupby('price').points.count,groupby是更常用的分类方法：根据某一个属性将数据条目分组，并在以属性为索引的子组中进行一些操作**
例如：按points分组，计算每组的成员数
```python
df.groupby('points').points.count()
```
又例如：按points分组，计算每组中的最低价格
```python
df.groupby('points').price.min()
```
**还可以结合apply进行组内筛选**
例如：找出每个酒评人最先品鉴的酒的名字
```python
df.groupby('winery').apply(lambda dataframe:dataframe.title.iloc[0])
```
**还可以进行更细的删选**


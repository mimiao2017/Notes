PandasLesson3_summary functions & map worbook
------------

求points这列的中位数
```
review.points.median()
```
求country这列中所有的国家
```
reviews.country.unique()
#返回的是一个array
```
求country这列中出现次数最多的国家
```
reviews.country.value_counts()
```
remap,将price这列remap为price-median
```
mp = reviews.price.median()
reviews.price.map(lambda v:v-mp)
```
按某种综合指标对wine进行排序，找到最高分的wine
```
reviews.loc[(reviews.points/reviews.price).idxmax()].title
#找到性价比（points/price）最高（idxmax）的红酒，并显示名字（title）
```
统计某个关键词在description这列出现的次数
``` pandas
t_wine=reviews.description.map(lambda r:"tropical" in r).value_counts()
#关键词tropical，生成的t_wine是Series类型,格式如下：
#False     378221
#True      908
```
清除数据中country列和variety列中的NaN，得到新数据集
```
reviews_new = reviews.loc[reviews.country.notnull() & reviews.variety.notnull()]
```
将两列数据相加????????????Q7
```
pd.Series([], index = )
```
map与apply

| map | apply |
| ------- | ------ |
| input:Series| input:DataFrame|
| `dataframe.points.map(lambda p:p-means)` | `datafram.apply(function,column='points') ` |   
|-|-|

注：
`def function(srs):
  srs.points = srs.points - review_points_mean 
  return srs`
  
一些快捷操作：
=====
* Series之间互相加减或者一个Series同时减去某个数：

  `df.points-menas`
  
  `df.points-df.extra`
  
* Series之间的+ ，-，<，>，==和字符串拼接等:

  `df.country+'-'+df.points`
  
  `Italy-29.5`

知识点
=====
* idxmax 与 argmax
* map()
* `!= 'NaN'`与`.notnull()`的区别

# Grouping

**summary中用到的`df.value_counts()`实际上是指向`df.groupby('price').points.count`,groupby是更常用的分类方法：根据某一个属性将数据条目分组，并在以属性为索引的子组中进行一些操作**

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
**还可以进行更细的筛选**

例如：根据国家和省份找出评分最高的酒
```python
reviews.groupby('country','province').apply(lambda df:df.iloc[df.points.argmax()])
```
得到的是出产自某个国家某个省份出产的所有酒中评分最高的酒的信息（所有国家与省份的组合都列出）

**还可以使用agg()展示某个组的详细参数**

例如：根据国家分组，得出各个国家产出的酒种的最高价、最低价、和长度？？
```python
reviews.groupby('country').price.agg([len,min,max])
```

## Multi-indexes

**待看pandas相关章节https://pandas.pydata.org/pandas-docs/stable/advanced.html**

**最常用reset_index()，用于将生成的结构复杂的dataframe拆解成一般格式**

例如：先生成一个有国家和省份两个复合index的dataframe，展示组内每个数据条目“描述”的长度,
再reset index
```python
country_reviews = reviews.groupby('country','province').discription.agg([len])
country_reviews.reset_index()
```

## Sorting

**将整个dataframe根据某一项参数进行排序**

**可以根据长度排序**

```python
df.sort_values(by='len')
```
`sort_values`默认是升序，可以通过`sort_values(by='len',ascending=False)`变为降序排序

**还可以将index排序**

`df.sort_index()`

**还可以对多个参数排序**

`df.sort_values(by=['country','len'])`





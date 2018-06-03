# 基本数据对象及操作
## 1.Series
> + 创建Series
    # 1
    import pandas as pd
    countries = ['中国', '美国', '澳大利亚']
    countries_s = pd.Series(countries)
    # 2
    country_dicts = {'CH': '中国',
                     'US': '美国',
                     'AU': '澳大利亚'}
    country_dict_S = pd.Series(country_dicts)
    #给索引命名
    country_dict_s.index.name = 'Code'
    #给数据命名
    country_dict_s.name = 'Country'
> + 处理缺失数据  
    字符串类型处理为None，数据类型处理为Nan
> + Series 索引  
    通过索引判断数据是否存在，使用in
    iloc 按index值索引，从0开始，如iloc[0]
    loc  按key值进行索引，如loc['key']
    或者直接['key’]索引
    也可以同时操作多个
    xxx.iloc[[0, 2, 5]]#例子
    xxx.loc[['a', 'b']]#  
> + 向量化操作

## 2.DataFrame
> + 创建DataFrame

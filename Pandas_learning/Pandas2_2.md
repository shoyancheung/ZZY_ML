## 数据清洗
### 1. 处理缺失数据
> + 判断数据缺失  
    XXX_data.isnull()#如果为nan则判断为True，否则为False  
    XXX_data.notnull()#如果数据不为nan则为True，否则为False  
    XXX_data.fillna(a)#将为nan的数据以a进行填充，a可以为数或字符
    XXX_data.dropna()#丢弃为空的数据
    XXX_data.ffill()#将nan值填充为前一个非nan的值
    XXX_data.bfill()#将nan值填充为后一个非nan的值
### 2. 数据变形
> + 处理重复数据  
    data.duplicated()#判断数据是否重复  
    data.drop_duplicates()#去除重复的数据  
    data.drop_duplicates(xx, keep = 'first/last')#丢弃重复的数据，不留第一个或者最后一个  
> + 使用函数或map转化数据  
    
    data = pd.DataFrame({'food':['bacon', 'pulled pork', 'Pastrami'], 'ounces': [4, 3, 6]})
    #添加一列，用于指定食物来源  
    meat_to_animal = {'bacon': 'pig', 'pulled pork': 'pig', 'pastrami': 'cow'}
    #使用map()  
    lowercased = data['food'].str.lower()  
    data['animal'] = lowercased.map(meat_to_animal)
    #或者使用以下方法
    data['animal1'] = data['food'].map(lambda x: meat_to_animal[x.lower()])  
> + 替换值  
    data.replace(anum, anewnum)#将anum全部替换为anewnum  
    data.replace([anum,..,nnum], newnum)#将[]全部替换为newnum
    ddata.replace([anum,..,nnum], [anewnum,.., nnewnum])#分别进行替换
    data.replace({anum:anewnum, bnum:bnewnum, ..})#同上  
> + 离散化和分箱操作  
    
    #年龄数据  
    ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
    #分箱边界
    bins = [18, 25, 35, 60, 100]
    cats = pd.cut(ages, bins)
    #cats [(18, 25], (18,25], (18, 25], (25, 35],...(25, 35]]
    #获取分箱编码
    cats.codes #array([0, 0, 0, 1, ..., 1], dtype = int8)
    #返回分箱边界索引
    cats.categories #IntervalIndex([(18, 25], (25, 35], (35, 60], (60, 100]]colsed = 'right', dtype = 'interval[int64]')
    #统计箱中元素的个数
    pd.value_counts(cats)#(18, 25]  5
    #带标签的分箱
    group_names = ['Youth', 'YoungAdult', 'MiddleAged', 'Senior']
    cats = pd.cut(ages, bins, labels = group_names)#array(['Youth', 'Youth', .. , 'YoungAdult'], dtype = object)
> + 哑变量操作
    
    df = pd.DataFrame({'key': ['b', 'b', 'a', 'c', 'a', 'b'], 'data1': range(6)})
    df 
    #  
         data1   key
     ---------------
     0    0      b
     1    1      b
     2    2      a
     3    3      c
     4    4      a
     5    5      b
    pd.get_dummies(df['key'])
    #
       a  b  c
    -----------
    0  0  1  0
    1  0  1  0
    2  1  0  0
    3  0  0  1
    4  1  0  0
    5  0  1  0
> + 向量化字符串操作
   
    

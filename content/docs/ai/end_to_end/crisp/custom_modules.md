---
title: 【0】自定义模块
weight: 1
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
math: true
---

<br>


<br>

## 1、模块概述

> 自定义模块是将平常使用到的模块进行封装，以便于重复使用。
> 主要目录如下：

{{< filetree/container >}}
  {{< filetree/folder name="MyPackage" state="open" >}}
    {{< filetree/file name="LICENSE" >}}
    {{< filetree/file name="README.md" >}}
    {{< filetree/file name="setup.py" >}}
    {{< filetree/folder name="DataScience" state="open" >}}
      {{< filetree/file name="\_\_init\_\_.py" >}}
      {{< filetree/file name="View.py" >}}
      {{< filetree/file name="EDA.py" >}}
    {{< /filetree/folder >}}
  {{< /filetree/folder >}}
{{< /filetree/container >}}


> ***下载解压后后放在 .ipynb 相同的文件夹下面就可以在 jupyter lab 笔记本中使用。***<br>
> 下载地址如下：

{{< cards >}}
  {{< card link="https://github.com/wenwangjain/wenwangjain.github.io" title="MyPackage" subtitle="" icon="package" >}}
{{< /cards >}}




<br><br><br>



## 2、View.py

### 2.1、View.title()

> ***简单的输出一个标题***

```python {linenos=table, linenostart=1}
def title(test):
    """
    打印标题信息。

    Args:
        test (str): 标题内容。

    Returns:
        None

    """
    print('\n')
    from rich.console import Console
    console=Console()
    console.print('  .:. ', test , ' .:.','\n' , "="*100 , style="bold green")    

```

<br><br>

### 2.2、View.df_border()

> ***对给定的 DataFrame `df` 进行样式设置，为表格头部 (th) 和表格数据 (td) 设置边框。***

```python {linenos=table, linenostart=1}
def df_border(df):
    """
    对给定的 DataFrame `df` 进行样式设置，为表格头部 (th) 和表格数据 (td) 设置边框。

    Args:
        df (pandas.DataFrame): 需要进行样式设置的 DataFrame。

    Returns:
        pandas.io.formats.style.Styler: 样式设置后的 DataFrame 视图。

    """
    view = df.style.format()\
    .set_table_styles([
        {'selector': 'th', 'props': [('border', '1px solid  #CACACA'), ('font-size', '11px'), ('font-weight', 'bold'), ('font-family', 'Georgia')]},  #('font-family', 'Georgia'),
        {'selector': 'td', 'props': [('border', '1px dashed #DEDEDE'), ('font-size', '12px'),]}  
        ])
    # ('font-family', 'Georgia')  \FangSong\Comic Sans MS
    # ('font-weight', 'bold')
    # ('border', '1px dashed #575454') \('border', '1px solid  #575454')
    # The border of the header (th) is set to a solid red line, and the border of the content section (td) of the table is set to a dashed green line.
    # ----------------------------------------------------------------------------------------------------
    # 表头（th）的边框设置为红色的实线（solid），表格的内容部分（td）的边框设置为绿色的虚线（dashed）。                 
    
    return view # .style.set_properties(**{'font-family': 'Georgia', 'font-size': '10pt'})
```

<br><br>

### 2.3、View.df_table()

> ***将输入的 DataFrame 转换成漂亮的表格并打印出来。***

```python {linenos=table, linenostart=1}
def df_table(df):
    """
    将输入的 DataFrame 转换成漂亮的表格并打印出来。

    Args:
        df (Any): 任意可以转换为 pandas DataFrame 的对象。

    Returns:
        None: 该函数直接打印格式化后的表格，无返回值。
    """
    import pandas as pd
    from tabulate import tabulate

    df = pd.DataFrame(df)
    print(tabulate(df
               , headers = "keys"
               , tablefmt = 'pretty' #pretty\psql\rounded_grid
               , floatfmt=".2f"
              )
        )
```

<br><br>

### 2.4、View.df_style()

```python {linenos=table, linenostart=1}
def df_style(df):
    from matplotlib.colors import ListedColormap,LinearSegmentedColormap

    clist1=['Coral', 'DimGray']
    clist2=['#519D9E', '#9DC8C8']
    clist3=['cornflowerblue', '#525252']
    clist4=['linen', 'Coral']

    newcmp1 = LinearSegmentedColormap.from_list('chaos',clist1)
    newcmp2 = LinearSegmentedColormap.from_list('chaos',clist2)
    newcmp3 = LinearSegmentedColormap.from_list('chaos',clist3)
    newcmp4 = LinearSegmentedColormap.from_list('chaos',clist4)
    
    view = df.style.background_gradient(cmap=newcmp4)\
        .set_table_styles([
            {'selector': 'th', 'props': [('border', '1px solid  #CACACA'), ('font-size', '11px'), ('font-weight', 'bold'), ('font-family', 'Georgia')]},  #('font-family', 'Georgia'),
            {'selector': 'td', 'props': [('border', '1px dashed #DEDEDE'), ('font-size', '12px'),]}  
            ])

    return view
```


<br><br><br>



## 3、EDA.py

### 3.1、EDA.des_table()

```python {linenos=table, linenostart=1}
def des_table(df, columns=None): # , decimal=2
    """
    生成数据框的描述性统计表格，包括数据类型、计数、缺失值、唯一值、偏度、峰度、异常值等统计量。
    
    Args:
    df: pandas DataFrame, 输入的待描述数据框。
    columns: List[str], 数据框各列的中文名称，如果传入则添加到结果数据框中，默认值为None。
    
    Returns:
    pandas.io.formats.style.Styler: 经过格式化并设置样式的描述性统计表格。
    """

    import warnings
    warnings.filterwarnings('ignore')

    from pandas import DataFrame
    import pandas as pd
    import numpy as np

    # pd.set_option('display.width', 0)  # 设置不换行
    pd.set_option('display.expand_frame_repr', False)

    # ----------------------------------------------------------------------------------------------------
    df_type = DataFrame(df.dtypes ,columns=['Dtypes'])#.reset_index()
    df_type['Explain_Chinese'] = columns
    #df_type.rename(columns={'index':'---feature_name---'},inplace=True)
    
    # ----------------------------------------------------------------------------------------------------
    df_count = pd.DataFrame(df.count(), columns=['count'])#.reset_index()
    df_isnull_sum = pd.DataFrame(df.isnull().sum(),columns=["null_cot"])#.reset_index()
    df_isnull_sum["null%"] = df_isnull_sum["null_cot"]/df.shape[0]

    # ----------------------------------------------------------------------------------------------------
    df_dtr = df.copy()
    for i in df_dtr.columns.tolist():
        df_dtr[i] = df_dtr[i].astype('str')
    df_dtr_des = df_dtr.describe(include='object').T
    df_dtr_des['top1%'] = df_dtr_des['freq']/df_dtr_des['count']
    df_dtr_des['Unique%'] = df_dtr_des['unique']/df_dtr_des['count']
    #df_dtr_des.rename(columns={'top':'top1', 'freq':'top1_freq'}, inplace = True)
    df_dtr_result = df_dtr_des[['unique', 'Unique%','top','freq','top1%']]#.reset_index()

    # ----------------------------------------------------------------------------------------------------
    df_des  = pd.DataFrame(df.describe().T).drop('count', axis=1)

    # ----------------------------------------------------------------------------------------------------
    df_flo = pd.DataFrame(df.dtypes, columns = ['dtypes']).reset_index()
    df_flo_list = df_flo.loc[(df_flo['dtypes'] != 'object'),'index'].values.tolist()
    
    df_flo_skew, df_flo_kurt = [], []
    for i in df_flo_list:
        df_flo_skew.append(df[i].skew())
        
    df_flo_kurt.append(df[i].kurt()-3)
    df_sk = pd.DataFrame(
         {'skewness':df_flo_skew, 'Kurtosis':df_flo_kurt}
        ,index = df_flo_list
        )

    # ----------------------------------------------------------------------------------------------------
    df_outlier = df.copy()
    name = []
    for i in df_flo_list:
        df_outlier[str(i)+"_IQR"] = df_outlier[i].quantile(q=0.75) - df_outlier[i].quantile(q=0.25)
        df_outlier[str(i)+"_1"] = np.where((df_outlier[i] < (df_outlier[i].quantile(q=0.25) - 1.5 * df_outlier[str(i)+"_IQR"])) | 
                                           (df_outlier[i] > (df_outlier[i].quantile(q=0.75) + 1.5 * df_outlier[str(i)+"_IQR"]))
                                            ,1,0)
        name.append(str(i)+"_1")

    df_o1 = df_outlier[name]
    df_o2 = pd.DataFrame(df_o1.sum(),columns=["IQR_outl"]).reset_index()
    df_o2["index"] = df_o2["index"].str.replace("_1","")
    df_o2.set_index('index', inplace=True)

    df_o2["IQR_outl%"] = df_o2["IQR_outl"]/df[df_flo_list].count()    

    # ----------------------------------------------------------------------------------------------------
    des_df = pd.concat(
         [df_type, df_count, df_isnull_sum, df_dtr_result, df_des, df_sk, df_o2]
        ,axis=1
        )
    #des_df.fillna('', inplace=True)
    des_df.reset_index(inplace=True)

    # ----------------------------------------------------------------------------------------------------
    des_df.rename(columns={
         'index':'Feature_Nname'
        ,'count':'Count'
        ,'null_cot':'Null_c-'
        ,'null%':'Null%'
        ,'unique':'Unique'
        ,'top':'Top_1_value'
        ,'top1%':'Top_1_c%'
        ,'freq':'Top_1_c'
        ,'mean':'Mean'
        ,'std':'Std'
        ,'min':'Min'
        ,'25%':'25%'
        ,'50%':'50%'
        ,'75%':'75%'
        ,'max':'Max'
        }
        ,inplace=True)

    des_df['Top_1_value'] = des_df['Top_1_value'].str.slice(0, 11)
        # ----------------------------------------------------------------------------------------------------
    name_describe = list(des_df.columns)[3:8] + list(des_df.columns)[9:]

    des_view = des_df.style.format({
         name_describe[2]:"{:.1%}",name_describe[4]:"{:.1%}",name_describe[6]:"{:.1%}"
        ,name_describe[7]:"{:.2f}",name_describe[8]:"{:.2f}",name_describe[9]:"{:.2f}",name_describe[10]:"{:.2f}",name_describe[11]:"{:.2f}",name_describe[12]:"{:.2f}",name_describe[13]:"{:.2f}"
        ,name_describe[14]:"{:.1f}",name_describe[15]:"{:.1f}"
        ,name_describe[16]:"{:.0f}",name_describe[17]:"{:.1%}"
        }
    ).bar( 
        color='Coral' #'lightcoral'
        ,subset=name_describe
        ,align='zero'
        ,height=80
        ,width=70
        )\
    .set_table_styles([
        {'selector': 'th', 'props': [('border', '1px solid  #CACACA'), ('font-size', '12px'), ('font-weight', 'bold')]},  #('font-family', 'Georgia'),
        {'selector': 'td', 'props': [('border', '1px dashed #DEDEDE'), ('font-size', '12px'),]}  
        ])
    # ('font-family', 'Georgia')  \FangSong\Comic Sans MS
    # ('font-weight', 'bold')
    # ('border', '1px dashed #575454') \('border', '1px solid  #575454')
    # The border of the header (th) is set to a solid red line, and the border of the content section (td) of the table is set to a dashed green line.
    # ----------------------------------------------------------------------------------------------------
    # 表头（th）的边框设置为红色的实线（solid），表格的内容部分（td）的边框设置为绿色的虚线（dashed）。                 
    
    return des_view # .style.set_properties(**{'font-family': 'Georgia', 'font-size': '10pt'})



```

<br><br>

### 3.2、EDA.des_chart()

```python {linenos=table, linenostart=1}
def des_chart(df):
    import numpy as np
    import matplotlib.pyplot as plt
    import seaborn as sns
    import scipy.stats as stats
    import math
    from statsmodels.distributions.empirical_distribution import ECDF
    import matplotlib
    
    plt.rcParams['font.sans-serif'] = ['FangSong'] # 设置中文黑体 SimHei
    plt.rcParams['axes.unicode_minus'] = False     # 设置显示负号
    
    
    #sns.set(style="white")
    matplotlib.rcdefaults()
    #plt.style.use('ggplot') # classic
    #sns.set(style="white")
    plt.rcParams['figure.dpi'] = 115 #分辨率
     
    df = df.fillna(value=0)
    dict_columns = df.dtypes.to_dict()
    
    font1 = {'fontproperties':'FangSong', 'fontweight': 'bold', 'size': 10, 'c':'k'} # 
    
    for i in df.columns:
        if str(dict_columns[i]) != 'object':
            fig = plt.figure(figsize=(13, 0.8))
      
            len_plot = 1/(13/1.5)
            typeface = 'FangSong'
            bins = 12
      
            left_1, width_1 = 0, len_plot*1.3  # left:左边、width:宽度
            left_2, width_2 = width_1+0.03, len_plot*1.6
            left_3, width_3 = left_2+width_2+0.03, len_plot*0.8
            left_4, width_4 = left_3+width_3+0.03, len_plot*0.8
            left_5, width_5 = left_4+width_4+0.03, len_plot*0.8
      
            bottom, height = 0, 0.6 # bottom:底部、height:高度
      
            rect_hist1 = [left_1, bottom, width_1, height+0.2]
            rect_hist2 = [left_2, bottom, width_2, height+0.2]
            rect_hist3 = [left_3, bottom, width_3, height+0.6]
            rect_hist4 = [left_4, bottom, width_4, height+0.6]
            rect_hist5 = [left_5, bottom, width_5, height+0.6]
    
            # --------------------------------------------------------------------------------
            ax_hist1 = plt.axes(rect_hist1)
            # --------------------------------------------------------------------------------
            plt.hist( df[i]
                      , bins=bins
                      #, density=1 #设置此项目可以使纵坐标显示频率
                      , facecolor="Coral" # 'lightcoral'/'coral'/'lightblue'/'cornflowerblue'
                      , edgecolor="white" # 条形边框颜色，不设置显示白色/white/indianred
                      )
            ax=plt.gca()
            ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
            ax.spines['right'].set_color('none')
            ax.spines['top'].set_color('none')
            ax.spines['left'].set_color('none')
            ax.spines['bottom'].set_linewidth(0.47)
            #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
            ax.spines["bottom"].set_position(("outward", 5))
            plt.yticks(fontproperties = typeface, size = 8)
            plt.xticks(fontproperties = typeface, size = 8) 
            #plt.title(i, font1) # , x=0.45, y=height+0.4 
            plt.title(i, size = 9
                   , fontproperties = 'FangSong'
                   , color = '#525252'
                   , fontweight='bold' 
                   , fontfamily='serif'
                  ) # fontproperties = 'FangSong',   
            plt.ticklabel_format(style='plain')
            
            # --------------------------------------------------------------------------------
            ax_hist2 = plt.axes(rect_hist2)
            # --------------------------------------------------------------------------------
            g1 = sns.kdeplot(df[i],linewidth = 1 ,c='DimGray') # DimGray\cornflowerblue
            #sns.despine() #可以自动隐藏上部（top）、右部（right）轴 #sns.despine( top=True, right=True)  #,bottom=True,left=True
            g1.set(xlabel=None)
            g1.set(ylabel=None)
            #g1.set(xticklabels=[]) 隐藏坐标轴标签 g1.set(yticklabels=[]) 
            plt.hist(df[i]
                      , bins=bins
                      , density=1 #设置此项目可以使纵坐标显示频率
                      , facecolor="Coral" # 'lightcoral'/'coral'/'lightblue'
                      , edgecolor="white" # 条形边框颜色，不设置显示白色/white/indianred
                      ) 
            ax=plt.gca()
            ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
            ax.spines['right'].set_color('none')
            ax.spines['top'].set_color('none')
            ax.spines['left'].set_color('none')
            ax.spines['bottom'].set_linewidth(0.47); 
            #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
            ax.spines["bottom"].set_position(("outward", 5)) 
            plt.yticks(fontproperties = typeface, size = 8)
            plt.xticks(fontproperties = typeface, size = 8) 
            plt.ticklabel_format(style='plain')
            
            # --------------------------------------------------------------------------------
            ax_hist3 = plt.axes(rect_hist3)
            # --------------------------------------------------------------------------------
            data = df[i].values
            ecdf = ECDF(data)
            cdf = ecdf(data)
            data.sort()
            cdf.sort()
            plt.scatter(data,cdf,c='DimGray',s=5) # cornflowerblue
            plt.plot(data,cdf,c='Coral',lw=1)
      
            ax=plt.gca()
            ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
            ax.spines['right'].set_linewidth(0.47) #设置坐标轴的粗细
            ax.spines['top'].set_linewidth(0.47)
            ax.spines['bottom'].set_linewidth(0.47)
            # ax.spines['right'].set_color('none')
            #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
            #ax.spines["bottom"].set_position(("outward", 5)) 
            #ax.spines["right"].set_position(("outward", 5))
            #ax.spines["top"].set_position(("outward", 5)) 
            plt.yticks(fontproperties = typeface, size = 8)
            plt.xticks(fontproperties = typeface, size = 8)
            plt.ylim(0,1)#X轴范围
            #data = churn["Account Length"]
            #if math.ceil(data.max()) < 0:
            #    good = - math.ceil(data.max())
            #else:
            #    good = math.ceil(data.max())
            #                         
            #hist, bin_edges = np.histogram(data, bins=good, density=True)# 计算随机数的频数分布
            #cdf = np.cumsum(hist * np.diff(bin_edges))# 计算随机数的累积分布函数
            #plt.plot(cdf, linewidth = 0.9)
            plt.ticklabel_format(style='plain')
            
            # --------------------------------------------------------------------------------
            ax_hist4 = plt.axes(rect_hist4)
            # --------------------------------------------------------------------------------
            data = df[i]
      
            mu, sigma = 0, 1
            np.random.seed(12345)
            x = np.random.normal(mu,sigma,size=len(data))
            x.sort()
            plt.scatter(x,data,c='DimGray',s=5) # cornflowerblue
            z = np.polyfit(x, data, 1)
            f = np.poly1d(z)
      
            # 绘制拟合线
            plt.plot(x,f(x),c='Coral', linewidth =1)
            ax=plt.gca()
            ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
            ax.spines['right'].set_linewidth(0.47) #设置坐标轴的粗细
            ax.spines['top'].set_linewidth(0.47)
            ax.spines['bottom'].set_linewidth(0.47)
            # ax.spines['right'].set_color('none')
            #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
            #ax.spines["bottom"].set_position(("outward", 5)) 
            #ax.spines["right"].set_position(("outward", 5))
            #ax.spines["top"].set_position(("outward", 5)) 
            plt.yticks(fontproperties = typeface, size = 8)
            plt.xticks(fontproperties = typeface, size = 8)
            plt.xlabel('')
            plt.ylabel('')
            plt.title('')

            plt.ticklabel_format(style='plain')
            #stats.probplot(churn["Account Length"], plot=plt,)
            # --------------------------------------------------------------------------------
            ax_hist5 = plt.axes(rect_hist5)
            # --------------------------------------------------------------------------------
            ax=plt.gca()
            #ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
            #ax.spines['right'].set_linewidth(0.47) #设置坐标轴的粗细
            #ax.spines['top'].set_linewidth(0.47)
            ax.spines['bottom'].set_linewidth(0.47)
            for i in ['left', 'right', 'top', 'bottom']:
                ax.spines[i].set_color('none')
            # ax.spines['right'].set_color('none')
            ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
            ax.spines["bottom"].set_position(("outward", 5)) 
            ax.spines["right"].set_position(("outward", 5))
            ax.spines["top"].set_position(("outward", 5)) 
            plt.yticks([], fontproperties = typeface, size = 8)
            plt.xticks([], fontproperties = typeface, size = 8)
            plt.xlabel('')
            plt.ylabel('')
            plt.title('')
    
            
            
        else:
            data1 = df[i].value_counts()[0:10]
            data2 = df[i].value_counts().cumsum()[0:10]/df.shape[0]
            x = [str(k) for k in data1.index]
            y =  data2.values
            z =  data1.values


            width = 5
            hight = 1.2
            
            
            
            from matplotlib import font_manager
            my_font=font_manager.FontProperties(fname="C:\Windows\Fonts\SIMYOU.TTF")
            
            plt.rcParams['axes.unicode_minus'] = False     # 设置显示负号
            
            fig, ax = plt.subplots(figsize=(width,hight))
            p1 = plt.bar(  x
                    , z
                    , facecolor="DimGray" # lightcoral\coral\cornflowerblue\lightblue
                    #, alpha=0.2
                    , width = 0.9
                   )
            
            plt.bar_label(p1, label_type='edge', fontproperties = my_font, size = 8, fontweight='bold')
            
            ax=plt.gca() 
            ax.spines['left'].set_color('none')
            ax.spines['right'].set_color('none')
            ax.spines['top'].set_color('none')
            ax.spines['bottom'].set_linewidth(0.47); #设置底部坐标轴的粗细
            ax.spines["bottom"].set_position(("outward", 5)) 
            plt.xticks(fontproperties = my_font, size = 8, rotation=60)
            plt.yticks([]) #fontproperties = 'Times New Roman', size = 8)
            #plt.title(i, size = 9)  
            
            
            ax_ = ax.twinx()
            plt.scatter(x,y,c='Coral',s=6)
            plt.plot(x,y,c='Coral',lw=0.8)
            
            ax_=plt.gca() 
            ax_.spines['left'].set_color('none')
            ax_.spines['right'].set_color('none')
            ax_.spines['top'].set_color('none')
            ax_.spines['bottom'].set_linewidth(0.47); #设置底部坐标轴的粗细
            ax_.spines["bottom"].set_position(("outward", 5))
            
            ax_.set_ylim((0,1.1))
            
            plt.yticks(fontproperties = 'Times New Roman', size = 8)
            plt.xticks(fontproperties = my_font, size = 8, rotation=60)
            #plt.title(i, size = 9)    
            
            #plt.title(i, font1, x=0.08, y=hight+0.05)
            plt.title(i, size = 9
                   , fontproperties = 'FangSong'
                   , color = '#525252'
                   , fontweight='bold' 
                   , fontfamily='serif'
                  ) # fontproperties = 'FangSong',   
            plt.show()

```

<br><br>

### 3.3、EDA.class_bar()

```python {linenos=table, linenostart=1}
def class_bar(df, category='barh', bar_width=30, alpha=1, stacked=True):
    import numpy as np
    import pandas as pd
    import matplotlib.pyplot as plt
    from pandas.plotting import table
    import matplotlib
    
    matplotlib.rcdefaults()
    pd.options.plotting.backend = 'matplotlib'
    #plt.rcParams['figure.dpi'] = 110 #分辨率
    
    #https://zhuanlan.zhihu.com/p/141251520
    import pylab 
    from matplotlib.colors import ListedColormap,LinearSegmentedColormap
    clist1=['Coral', 'DimGray']
    clist2=['#519D9E', '#9DC8C8']
    clist3=['cornflowerblue', '#525252']
    newcmp1 = LinearSegmentedColormap.from_list('chaos',clist1)
    newcmp2 = LinearSegmentedColormap.from_list('chaos',clist2)
    newcmp3 = LinearSegmentedColormap.from_list('chaos',clist3)
    
    if category == 'barh':
        l = df.shape[0]
        fig, ax = plt.subplots(figsize=(8, l*0.4))
        
        # ----------------------------------------------------------------------------------------------------
        df.plot.barh(
                      width=1#0.95 #height=1  # ax.bar(width=0.5)
                    , alpha=alpha
                    , edgecolor="white"
                    , cmap=newcmp1 #, color ='cadetblue'\viridis
                    , stacked=stacked 
                    , ax=ax
                    )    
        
        # ----------------------------------------------------------------------------------------------------
        ax=plt.gca()
        
        #Set the thickness of the coordinate axis
        #设置坐标轴的粗细
        for i in ['left', 'bottom']:
            ax.spines[i].set_linewidth(0.37) 

        #Hide axes
        # 隐藏坐标轴
        for j in ['right', 'top']:
            ax.spines[j].set_color('none')

        # Set axis position
        # 设置坐标轴位置
        ax.spines["left"].set_position(("outward", 5)) 
        ax.spines["bottom"].set_position(("outward", 2)) 
        
     
        # ----------------------------------------------------------------------------------------------------
        # https://www.zhihu.com/question/358110422#:~:text=%E6%88%96%E8%80%85%EF%BC%8C%E5%A6%82%E6%9E%9C%E4%BD%A0%E5%8F%AA%E6%98%AF%E6%83%B3%E4%B8%B4%E6%97%B6%E4%BF%AE%E6%94%B9%EF%BC%8C%E9%82%A3%E4%B9%88%E5%B0%B1%E5%9C%A8%E7%BB%98%E5%9B%BE%E5%89%8D%EF%BC%8C%E7%94%A8%20plt.rcParams%20%5B%27font.sans-serif%27%5D%20%3D%20%5B%27Times,New%20Roman%27%5D%20%E8%BF%99%E6%A0%B7%E7%9A%84%E6%96%B9%E5%BC%8F%E5%B0%86%20font.sans-serif%20%E8%BF%99%E4%B8%AA%E5%B1%9E%E6%80%A7%E9%87%8C%E9%9D%A2%E7%9A%84%E5%86%85%E5%AE%B9%EF%BC%8C%E6%9B%BF%E6%8D%A2%E4%B8%BA%E4%BD%A0%E6%83%B3%E8%A6%81%E7%9A%84%E5%AD%97%E4%BD%93%E5%8D%B3%E5%8F%AF%E3%80%82
        legend_font = {"family" : "Times New Roman", 'weight':'bold', 'size':9}
        leg = plt.legend(
             bbox_to_anchor=(1.05, 0)
            , loc=3
            , borderaxespad=0
            , frameon=True
            , prop=legend_font
            ).get_frame()
        leg.set_linewidth(0.37)
        #leg.set_color('#525252') # background color背景颜色

        # ----------------------------------------------------------------------------------------------------
        plt.yticks(fontproperties = 'FangSong', size = 10) # fontproperties = 'Times New Roman',
        plt.xticks(fontproperties = 'FangSong', size = 9, rotation=60)  
        plt.xlabel('') #(df.columns[0], size = 11) # fontproperties = 'Times New Roman',
        plt.ylabel(df.index.name, size = 12
                   , fontproperties = 'FangSong'
                   , color = '#525252'
                   , fontweight='bold' 
                   , fontfamily='serif'
                  ) 
        #plt.text(0, 1.1
        #        , title=title
        #        , fontsize=20
        #        , fontweight='bold'
        #        , fontfamily='serif'
        #        , color = '#525252'
        #        )
        plt.show()
        
    elif category == 'bar':
        fig, ax = plt.subplots(figsize=(bar_width*0.4, 3))

        df.plot.bar(
                      width=1#0.99 #height=1  # ax.bar(width=0.5)
                    , alpha=alpha
                    , edgecolor="white"
                    , cmap=newcmp1 #, color ='cadetblue'\viridis
                    , stacked=stacked 
                    , ax=ax
                    )    

        ax=plt.gca()
        ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
        ax.spines['right'].set_color('none')
        ax.spines['top'].set_color('none')
        ax.spines['bottom'].set_linewidth(0.47)
        ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
        ax.spines["bottom"].set_position(("outward", 2)) # 设置坐标轴位置  
        
    
        legend_font = {"family" : "Times New Roman", 'weight':'bold', 'size':9}
        leg = plt.legend(bbox_to_anchor=(1.05, 0)
                    , loc=3
                    , borderaxespad=0
                    , frameon=True
                    , prop=legend_font
                  ).get_frame()
        leg.set_linewidth(0.37)
        #leg.set_color('#525252') #背景颜色
    
        plt.yticks(fontproperties = 'FangSong', size = 10) # fontproperties = 'Times New Roman',
        plt.xticks(fontproperties = 'FangSong', size = 9, rotation=60)  # fontproperties = 'Times New Roman',
        plt.xlabel('')#(df.columns[0], size = 11) # fontproperties = 'Times New Roman',
        plt.ylabel(df.index.name, size = 12
                   , fontproperties = 'FangSong'
                   , color = '#525252'
                   , fontweight='bold' 
                   , fontfamily='serif'
                  )
        #plt.text(0, 1.1
        #         , title=title
        #         , fontsize=20
        #         , fontweight='bold'
        #         , fontfamily='serif'
        #         , color = '#525252'
        #        )
        plt.show()
        
    else:
        print("Plise argument 'category', value: 'barh' or 'bar'")
```

<br><br>

### 3.4、EDA.class_pie()

```python {linenos=table, linenostart=1}
def class_pie(df):
    import matplotlib.pyplot as plt

    plt.rcParams['font.sans-serif']=['FangSong'] # 用来正常显示中文标签
    plt.rcParams['axes.unicode_minus']=False # 用来正常显示负号

    import pylab 
    from matplotlib.colors import ListedColormap,LinearSegmentedColormap

    clist1=['Coral', 'DimGray']
    clist2=['#519D9E', '#9DC8C8']
    clist3=['cornflowerblue', '#525252']
    newcmp1 = LinearSegmentedColormap.from_list('chaos',clist1)
    newcmp2 = LinearSegmentedColormap.from_list('chaos',clist2)
    newcmp3 = LinearSegmentedColormap.from_list('chaos',clist3)

    out = df.plot.pie(
             autopct='%1.2f%%'
            ,figsize = (3,3)
            ,cmap=newcmp1 #, color ='cadetblue'\viridis
            ,subplots=True
        ,legend=False
        )

    plt.ylabel(
         df.index.name
        ,size = 12
        ,fontproperties = 'FangSong'
        ,color = '#525252'
        ,fontweight='bold' 
        ,fontfamily='serif'
        )
    
    plt.show()
    
    return out
```

<br><br>

### 3.5、EDA.class_table()

```python {linenos=table, linenostart=1}
def class_table(df, values=['index'], index=[], columns=[]):
    import pandas as pd
    
    df = df.reset_index()

    col_len = df[columns].value_counts().shape[0]

    # ----------------------------------------------------------------------------------------------------
    df_table = df.pivot_table(
         values = values
        ,index = index
        ,columns=columns
        ,margins=True
        ,aggfunc=len
        )

    # ----------------------------------------------------------------------------------------------------
    columns_list = df_table.columns
    columns_df = columns_list.droplevel(None)
    df_table.columns = columns_df

    for i in columns_df.tolist():
        df_table[str(i)+"_row_pro"] = df_table[i]/df_table['All']

    for j in columns_df.tolist():
        if len(index) > 1:
            col_all = df_table.loc["All",j].values[0]
        else: 
            col_all = df_table.loc["All",j]
            
        df_table[str(j)+"_clo_pro"] = df_table[j]/col_all

    df_table_value = pd.DataFrame(df_table.iloc[:-1,0:col_len])
    df_table_propration = pd.DataFrame(df_table.iloc[:-1,col_len+1:col_len*2+1])
    
    return df_table, df_table_value, df_table_propration
```

<br><br>

### 3.6、EDA.corr_heatmap()

```python {linenos=table, linenostart=1}
def corr_heatmap(df):
    import numpy as np
    import pandas as pd
    import seaborn as sns
    import matplotlib
    import matplotlib.pyplot as plt

    from matplotlib.colors import ListedColormap,LinearSegmentedColormap
    clist1=['Coral', '#FFFFFF', 'DimGray']
    clist2=['#519D9E', '#9DC8C8']
    clist3=['cornflowerblue', '#525252']
    newcmp1 = LinearSegmentedColormap.from_list('chaos',clist1)
    newcmp2 = LinearSegmentedColormap.from_list('chaos',clist2)
    newcmp3 = LinearSegmentedColormap.from_list('chaos',clist3)

    dict_columns = df.dtypes.to_dict()
    cols = []
    for i in df.columns:
        if str(dict_columns[i]) != 'object':
            cols.append(i)

    cols_len = len(cols)

    #https://zhuanlan.zhihu.com/p/96040773

    matplotlib.rcdefaults()

    len_value = len(cols)/1.2                               # 此项可以动态绘制大小
    fig,ax=plt.subplots(figsize=(len_value, len_value-0.6)) # 设置大小


    corr = np.corrcoef(df[cols].values.T)   # 求相关矩阵
    mask = np.zeros_like(corr)              # 首先来生成Mask矩阵
    mask[np.triu_indices_from(mask)] = True # 使用np.triu函数可以返回上三角矩阵对应的 Mask


    s = sns.heatmap(corr
                , mask=mask               # 显示下半部分
                , annot=True              # 显示相关系数值
                , fmt='.2f'               # 相关系数值格式
                , annot_kws={'size': 10}  # 文本格式\大小
                #, linewidths=.01          # 设置每个单元格边框的宽度
                #, cmap=sns.diverging_palette(220, 20, sep=10, as_cmap=True) 
                #, cmap=sns.diverging_palette(0, 230, 90, 60, as_cmap=True)
                , cmap = newcmp1          # 颜色条 "RdBu_r\"RdBu_r\Blues     
                , vmin=-1                 # 颜色条最大值
                , vmax= 1                 # 颜色条最小值
                , cbar_kws={"shrink": .6} # 颜色条大小\图例大小
                            , square=True             # 标签横向排列
                )


    s.set_xticklabels(cols, fontproperties='Times New Roman', size=9, weight='bold', c='dimgray')
    s.set_yticklabels(cols, fontproperties='Times New Roman', size=9, weight='bold', c='dimgray') #SimHei/FangSong

    cbar = plt.gcf().axes[-1]
    cbar.tick_params(labelsize=9 # 颜色条字体大小
                    , width=1   # 颜色条指示线宽度
                    , length=1  # 颜色条指示线长度
                    )

    #cax.tick_params(labelsize=9, fontproperties='Times New Roman')

    ax.set_xticklabels(s.get_xticklabels(), rotation=30)
    ax.set_yticklabels(s.get_yticklabels(), rotation=0)

    plt.show()
```

<br><br><br>



## 4、Model.py

### 4.1、metrics_con_matrix()

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.metrics import confusion_matrix
from matplotlib.colors import LinearSegmentedColormap

def metrics_con_matrix(real_label, prediction_label, size = 3, serif='FangSong', cmap_color = ['#F5F5F5', 'DimGrey'], rgb_color = (237/255, 243/255, 238/255)):
    # real_label = real_label
    # prediction_label = prediction_label
    # serif = 'FangSong' # \'SimHei'\'FangSong'\'Georgia'
    # cmap_color = ['#FFFFFF', 'DimGrey'] # '#FFFFFF', 'DimGray'
    # rgb_color = (237/255, 243/255, 238/255)  # 将每个值除以 255 进行归一化

    # import numpy as np
    # import matplotlib.pyplot as plt
    # from sklearn.metrics import confusion_matrix

    plt.rcParams['font.sans-serif']=[serif]    # 替换sans-serif字体，正常显示中文(黑体)\'SimHei'\'FangSong'\'Georgia'
    plt.rcParams["font.weight"] = "bold"      # 字体加粗
    plt.rcParams['axes.unicode_minus'] = False # 坐标显示负号

    #from matplotlib.colors import LinearSegmentedColormap
    cmap = LinearSegmentedColormap.from_list('chaos',cmap_color)


    con_matrix = confusion_matrix(real_label, prediction_label)
    
    fig, ax = plt.subplots(figsize=(3.5+size,3+size))
    ax.set_facecolor(rgb_color) # 设置坐标轴的背景颜色
    fig.patch.set_facecolor(rgb_color) # 设置整个图形的背景颜色

    im = ax.imshow(con_matrix, interpolation='nearest', cmap=cmap) # cmap=plt.cm.Blues
    cbar = fig.colorbar(im, shrink=0.7)  # shrink 参数控制大小，0.5 表示缩小为原来的一半

    ax.set_title('Confusion Matrix')  # 设置标题
    ax.set_xlabel('Prediction Label') # 设置 x 轴标签
    ax.set_ylabel('Real Label') # 设置 y 轴标签

    ax.set_xticks(range(len(np.unique(real_label))), np.unique(real_label))
    ax.set_yticks(range(len(np.unique(real_label))), np.unique(real_label))

    for i in range(con_matrix.shape[0]):
        for j in range(con_matrix.shape[1]):
            ax.text(j, i, str(con_matrix[i, j]), horizontalalignment="center", color="white" if con_matrix[i, j] > con_matrix.max() / 2 or con_matrix[i, j]==0  else "black")

    plt.show()
```



<br><br><br>









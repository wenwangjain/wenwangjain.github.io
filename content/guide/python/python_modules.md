---
title: Python 内置模块
weight: 202
#next: /guide
prev: /guide
#editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---

## **os**

### os.getcwd()

```python {linenos=table, linenostart=1}
  import os
  os.getcwd()                         # 获取当前工作空间/目录
```


<br><br>



### os.mkdir()

```python {linenos=table, linenostart=1}
  import os
  os.mkdir("PASH")                    # 新建目录
```



<br><br>



### os.chdir()

```python {linenos=table, linenostart=1}
  import os
  os.chdir("PATH")                    # 切换新都工作空间
```



<br><br>



### os.listdir()

```python {linenos=table, linenostart=1}
  import os
  os.listdir("PATH")                  # 列出当前工作空间文件/文件夹
```



<br><br>




### os.path.splitext()

```python {linenos=table, linenostart=1}
  import os
  os.path.splitext("PATH")            # 分离文件名和扩展名

  # 输出案例：
  # ('input\11595\train', '.csv')
```

```python {linenos=table, linenostart=1, filename=""}
  _, file_type = os.path.splitext(path_file)
  # 其中的 _ 是一个常规的 Python 变量，并且它被用来存储分离的文件名部分。
  # 由于文件名部分在这个语句中并不需要，所以采用了 _ 作为变量名，以表示这个值会被忽略。
  file_type
  
  # 输出：
  # '.csv'
```



<br><br>



### os.path.join()

```python {linenos=table, linenostart=1}
  import os
  os.path.join('input', '11595', 'train.csv')   # 拼接多个目录\文件夹名称，文件名

  # 输出案例：
  # input\11595\train.csv
```


<br><br>



### os.walk()

  ```python {linenos=table, linenostart=1, filename="example 2"}
  import os
    
  path_join = os.path.join('input', '11595')
    
  for dirname, _, filenames in os.walk(path_join):
      for filename in filenames:
          print(os.path.join(dirname, filename))

  # 输出案例：
  # input\11595\sample_submission.csv
  # input\11595\sample_submission.csv.zip
  # input\11595\test.csv
  # input\11595\test.csv.zip
  # input\11595\train.csv
  # input\11595\train.csv.zip
  ```







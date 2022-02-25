# 展示书籍列表 {#展示书籍列表}

## 需求 {#需求}

![](/assets/list.png)

## 实现步骤 {#实现步骤}

* 1.创建视图
* 2.创建模板
* 3.配置URLconf

#### 1.创建视图 {#1创建视图}

* 查询数据库数据
* 构造上下文
* 传递上下文到模板

  ```
  # 定义视图：提供书籍列表信息
  def bookList(request):
      # 查询数据库书籍列表数据
      books = BookInfo.objects.all()
      # 构造上下文
      context = {'books':books}
      # 数据交给模板处理，处理完成后通过视图响应给客户端
      return render(request, 'Book/booklist.html', context)
  ```

#### 2.创建模板 {#2创建模板}

* 读取上下文数据
* 构造网页html文档 : 书籍信息以列表样式展示

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>书籍列表信息</title>
</head>
<body>

<ul>
    {% for book in books %}
        <li>{{ book.name }}</li>
    {% endfor %}
</ul>
</body>
</html>
```

#### 3.配置URLconf {#3配置urlconf}

* 进入`应用`中的`urls.py`文件

  ```
  from django.conf.urls import url
  from book.views import index,bookList

  urlpatterns = [
      url(r'^$',index),
      # 匹配书籍列表信息的URL,调用对应的bookList视图
      url(r'^booklist/$',bookList)
  ]
  ```




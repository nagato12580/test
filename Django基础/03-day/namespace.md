## 路由命名 {#3-路由命名与reverse反解析（逆向）}

在定义路由的时候，可以为路由命名，方便查找特定视图的具体路径信息。

1\) 在使用include函数定义路由时，可以使用namespace参数定义路由的命名空间，如

```py
path('',include('book.urls',namespace='book'))
```

命名空间表示，凡是book.urls中定义的路由，均属于namespace指明的book名下。

**命名空间的作用：避免不同应用中的路由使用了相同的名字发生冲突，使用命名空间区别开。**

2\) 在定义普通路由时，可以使用name参数指明路由的名字，如

```py
from django.urls import path
from book.views import index

urlpatterns = [
    path('index/',index,name='home')
]
```




# 编写你的第一个 Django 应用程序，第 1 部分[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#writing-your-first-django-app-part-1)

让我们通过例子来学习。

在本教程中，我们将引导您完成基本民意调查应用程序的创建。

它将由两部分组成：

- 一个允许人们查看民意调查并投票的公共网站。
- 允许您添加、更改和删除投票的管理站点。

我们假设您已经[安装了 Django](https://docs.djangoproject.com/en/5.0/intro/install/)。您可以通过在 shell 提示符下运行以下命令（由 $ 前缀表示）来判断已安装 Django 以及哪个版本：

```
$ python -m django --version
```

如果安装了 Django，您应该会看到安装的版本。如果不是，您将收到一条错误消息“没有名为 django 的模块”。

本教程是为 Django 5.0 编写的，它支持 Python 3.10 及更高版本。如果 Django 版本不匹配，您可以使用本页右下角的版本切换器参考您的 Django 版本的教程，或者将 Django 更新到最新版本。如果您使用的是较旧版本的 Python，请检查[我可以将哪个 Python 版本与 Django 一起使用？](https://docs.djangoproject.com/en/5.0/faq/install/#faq-python-version-support)找到 Django 的兼容版本。

请参阅[如何安装 Django，](https://docs.djangoproject.com/en/5.0/topics/install/)获取有关如何删除旧版本 Django 并安装新版本的建议。

从哪里获得帮助：

如果您在完成本教程时遇到问题，请转到常见问题解答的[“获取帮助”](https://docs.djangoproject.com/en/5.0/faq/help/)部分。



## 创建项目[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#creating-a-project)

如果这是您第一次使用 Django，您将必须进行一些初始设置。也就是说，您需要自动生成一些代码来建立 Django[项目](https://docs.djangoproject.com/en/5.0/glossary/#term-project)- Django 实例的设置集合，包括数据库配置、特定于 Django 的选项和特定于应用程序的设置。

从命令行`cd`进入您要存储代码的目录，然后运行以下命令：

/

 



```
$ django-admin startproject mysite
```

这将在您的当前目录中创建一个`mysite`目录。如果它不起作用，请参阅[运行 django-admin 时遇到的问题](https://docs.djangoproject.com/en/5.0/faq/troubleshooting/#troubleshooting-django-admin)。

笔记

您需要避免在内置 Python 或 Django 组件之后命名项目。特别是，这意味着您应该避免使用诸如 `django`（这将与 Django 本身冲突）或`test`（这与内置 Python 包冲突）之类的名称。

这段代码应该放在哪里？

如果您的背景是普通的旧 PHP（没有使用现代框架），您可能习惯将代码放在 Web 服务器的文档根目录下（在诸如 的位置`/var/www`）。使用 Django，你就不会这样做。将任何此类 Python 代码放入 Web 服务器的文档根目录中都不是一个好主意，因为这存在人们可能能够通过 Web 查看您的代码的风险。这对安全不利。

将代码放在文档根目录**之外**的某个目录中，例如 `/home/mycode`.

让我们看看[`startproject`](https://docs.djangoproject.com/en/5.0/ref/django-admin/#django-admin-startproject)创建了什么：

```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```

这些文件是：

- 外部`mysite/`根目录是您的项目的容器。它的名字对 Django 来说并不重要；重要的是它的名字。您可以将其重命名为您喜欢的任何名称。
- `manage.py`：一个命令行实用程序，可让您以各种方式与此 Django 项目交互。您可以`manage.py`在[django-admin 和 manage.py](https://docs.djangoproject.com/en/5.0/ref/django-admin/)中阅读有关的所有详细信息 。
- 内部`mysite/`目录是项目的实际 Python 包。它的名称是您需要用来导入其中任何内容的 Python 包名称（例如`mysite.urls`）。
- `mysite/__init__.py`：一个空文件，告诉 Python 该目录应被视为 Python 包。如果您是 Python 初学者，请阅读官方 Python 文档中[有关包的更多信息。](https://docs.python.org/3/tutorial/modules.html#tut-packages)
- `mysite/settings.py`：此 Django 项目的设置/配置。 [Django 设置](https://docs.djangoproject.com/en/5.0/topics/settings/)将告诉您有关设置如何工作的所有信息。
- `mysite/urls.py`：该 Django 项目的 URL 声明； Django 驱动的网站的“目录”。您可以在[URL 调度程序](https://docs.djangoproject.com/en/5.0/topics/http/urls/)中阅读有关 URL 的更多信息。
- `mysite/asgi.py`：与 ASGI 兼容的 Web 服务器的入口点，为您的项目提供服务。有关更多详细信息，请参阅[如何使用 ASGI 进行部署](https://docs.djangoproject.com/en/5.0/howto/deployment/asgi/)。
- `mysite/wsgi.py`：与 WSGI 兼容的 Web 服务器为您的项目提供服务的入口点。有关更多详细信息，请参阅[如何使用 WSGI 进行部署](https://docs.djangoproject.com/en/5.0/howto/deployment/wsgi/)。



## 开发服务器[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#the-development-server)

让我们验证您的 Django 项目是否有效。`mysite`如果还没有更改到外部目录，请运行以下命令：

```
$ python manage.py runserver
```

您将在命令行上看到以下输出：

```
正在执行系统检查...

系统检查未发现任何问题（0 已静音）。

您有未应用的迁移；在应用它们之前，您的应用程序可能无法正常工作。
运行“python manage.py migrate”来应用它们。

2024 年 3 月 29 日 - 15:50:53
Django 版本 5.0，使用设置“mysite.settings”在http://127.0.0.1:8000/
启动开发服务器
使用 CONTROL-C 退出服务器。
```

笔记

暂时忽略有关未应用的数据库迁移的警告；我们很快就会处理数据库。

您已经启动了 Django 开发服务器，这是一个纯粹用 Python 编写的轻量级 Web 服务器。我们已将其包含在 Django 中，以便您可以快速开发内容，而无需处理配置生产服务器（例如 Apache），直到您准备好进行生产为止。

现在是注意的好时机：**不要**在任何类似于生产环境的地方使用此服务器。它仅供开发时使用。 （我们的业务是制作 Web 框架，而不是 Web 服务器。）

现在服务器已运行，请使用 Web 浏览器访问http://127.0.0.1:8000/ 。您会看到“恭喜！”页面，火箭起飞。有效！

更改端口

默认情况下，该[`runserver`](https://docs.djangoproject.com/en/5.0/ref/django-admin/#django-admin-runserver)命令在内部 IP 的端口 8000 上启动开发服务器。

如果要更改服务器的端口，请将其作为命令行参数传递。例如，此命令在端口 8080 上启动服务器：

```
$ python manage.py runserver 8080
```

如果要更改服务器的 IP，请将其与端口一起传递。例如，要监听所有可用的公共 IP（如果您正在运行 Vagrant 或想要在网络上的其他计算机上展示您的工作，这很有用），请使用：

```
$ python manage.py runserver 0.0.0.0:8000
```

开发服务器的完整文档可以在参考中找到 [`runserver`](https://docs.djangoproject.com/en/5.0/ref/django-admin/#django-admin-runserver)。

自动重新加载[`runserver`](https://docs.djangoproject.com/en/5.0/ref/django-admin/#django-admin-runserver)

开发服务器根据需要自动为每个请求重新加载Python代码。您无需重新启动服务器即可使代码更改生效。但是，某些操作（例如添加文件）不会触发重新启动，因此在这些情况下您必须重新启动服务器。



## 创建投票应用程序[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#creating-the-polls-app)

现在您的环境（一个“项目”）已经设置完毕，您就可以开始工作了。

您在 Django 中编写的每个应用程序都包含一个遵循特定约定的 Python 包。 Django 附带了一个实用程序，可以自动生成应用程序的基本目录结构，因此您可以专注于编写代码而不是创建目录。

项目与应用程序

项目和应用程序有什么区别？应用程序是一种执行某些操作的网络应用程序，例如博客系统、公共记录数据库或小型民意调查应用程序。项目是特定网站的配置和应用程序的集合。一个项目可以包含多个应用程序。一个应用程序可以位于多个项目中。

您的应用程序可以位于[Python 路径](https://docs.python.org/3/tutorial/modules.html#tut-searchpath)上的任何位置。在本教程中，我们将在与您的文件相同的目录中创建投票应用程序 `manage.py`，以便可以将其作为自己的顶级模块导入，而不是作为`mysite`.

要创建您的应用程序，请确保您位于同一目录中`manage.py` 并输入以下命令：

```
$ python manage.py startapp polls
```

这将创建一个目录`polls`，其布局如下：

```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

该目录结构将容纳投票应用程序。



## 写下你的第一个视图[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#write-your-first-view)

我们来写第一个视图。打开该文件`polls/views.py` 并将以下 Python 代码放入其中：

`polls/views.py`[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#id1)

```
from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

这是 Django 中最简单的视图。要调用视图，我们需要将其映射到 URL - 为此我们需要一个 URLconf。

要在 polls 目录中创建 URLconf，请创建一个名为`urls.py`.您的应用程序目录现在应如下所示：

```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    urls.py
    views.py
```

在该`polls/urls.py`文件中包含以下代码：

`polls/urls.py`[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#id2)

```
from django.urls import path

from . import views

urlpatterns = [
    path("", views.index, name="index"),
]
```

下一步是将根 URLconf 指向`polls.urls`模块。在 中 `mysite/urls.py`，添加导入并在列表中`django.urls.include`插入 an ，这样您就拥有：[`include()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.include)`urlpatterns`

`mysite/urls.py`[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#id3)

```
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("polls/", include("polls.urls")),
    path("admin/", admin.site.urls),
]
```

该[`include()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.include)函数允许引用其他 URLconf。每当 Django 遇到 时[`include()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.include)，它都会截掉 URL 中与该点匹配的任何部分，并将剩余的字符串发送到包含的 URLconf 进行进一步处理。

其背后的想法[`include()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.include)是让即插即用的 URL 变得容易。由于民意调查位于其自己的 URLconf ( `polls/urls.py`) 中，因此可以将它们放置在“/polls/”下、“/fun_polls/”下、“/content/polls/”下或任何其他路径根下，并且应用程序仍将工作。

何时使用[`include()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.include)

`include()`当包含其他 URL 模式时应 始终使用。`admin.site.urls`是唯一的例外。

您现在已将`index`视图连接到 URLconf 中。使用以下命令验证它是否正常工作：

```
$ python manage.py runserver
```

在浏览器中访问http://localhost:8000/polls/，您应该会看到文本“ *Hello, world.您位于民意调查索引处。* ”，您在 `index`视图中定义的。

找不到网页？

如果您在此处收到错误页面，请检查您是否要访问 http://localhost:8000/polls/而不是http://localhost:8000/。

该[`path()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.path)函数传递四个参数，其中两个是必需的： `route`和`view`，两个可选的：`kwargs`, 和`name`。此时，值得回顾一下这些论点的目的。



### [`path()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.path)争论：`route`[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#path-argument-route)

`route`是包含 URL 模式的字符串。处理请求时，Django 从第一个模式开始，沿着`urlpatterns`列表向下移动，将请求的 URL 与每个模式进行比较，直到找到匹配的模式。

模式不搜索 GET 和 POST 参数或域名。例如，在对 的请求中`https://www.example.com/myapp/`，URLconf 将查找 `myapp/`。在发出请求时`https://www.example.com/myapp/?page=3`，URLconf 也会查找`myapp/`。



### [`path()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.path)争论：`view`[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#path-argument-view)

当 Django 找到匹配模式时，它会调用指定的视图函数，并将[`HttpRequest`](https://docs.djangoproject.com/en/5.0/ref/request-response/#django.http.HttpRequest)对象作为第一个参数，并将路由中的任何“捕获”值作为关键字参数。稍后我们将给出一个例子。



### [`path()`](https://docs.djangoproject.com/en/5.0/ref/urls/#django.urls.path)争论：`kwargs`[¶](https://docs.djangoproject.com/en/5.0/intro/tutorial01/#path-argument-kwargs)

任意关键字参数可以通过字典传递到目标视图。我们不会在本教程中使用 Django 的此功能。
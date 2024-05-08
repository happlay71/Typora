# 快速安装指南[¶](https://docs.djangoproject.com/en/5.0/intro/install/#quick-install-guide)

在使用 Django 之前，您需要先安装它。我们有 [完整的安装指南](https://docs.djangoproject.com/en/5.0/topics/install/)，涵盖了所有可能性；本指南将指导您进行最小化安装，在您完成介绍时可以正常工作。



## 安装Python [¶](https://docs.djangoproject.com/en/5.0/intro/install/#install-python)

作为一个 Python Web 框架，Django 需要 Python。请参阅 [我可以将哪个 Python 版本与 Django 一起使用？](https://docs.djangoproject.com/en/5.0/faq/install/#faq-python-version-support)了解详情。 Python 包含一个名为[SQLite](https://www.sqlite.org/)的轻量级数据库，因此您还不需要设置数据库。

[从https://www.python.org/downloads/](https://www.python.org/downloads/)或使用操作系统的包管理器获取最新版本的 Python 。

`python`您可以通过在 shell 中输入来验证 Python 是否已安装；你应该看到类似的东西：

```
Python 3.x.y
[GCC 4.x] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```



## 设置数据库[¶](https://docs.djangoproject.com/en/5.0/intro/install/#set-up-a-database)

仅当您想使用“大型”数据库引擎（如 PostgreSQL、MariaDB、MySQL 或 Oracle）时才需要执行此步骤。要安装此类数据库，请查阅[数据库安装信息](https://docs.djangoproject.com/en/5.0/topics/install/#database-installation)。



## 安装 Django [¶](https://docs.djangoproject.com/en/5.0/intro/install/#install-django)

您可以通过三个选项来安装 Django：

- [安装官方版本](https://docs.djangoproject.com/en/5.0/topics/install/#installing-official-release)。对于大多数用户来说，这是最好的方法。
- [安装您的操作系统发行版提供的](https://docs.djangoproject.com/en/5.0/topics/install/#installing-distribution-package)Django 版本。
- [安装最新的开发版本](https://docs.djangoproject.com/en/5.0/topics/install/#installing-development-version)。此选项适合想要最新、最强大的功能并且不害怕运行全新代码的爱好者。您可能会在开发版本中遇到新的错误，但是报告它们有助于 Django 的开发。此外，与最新稳定版本相比，第三方软件包的版本与开发版本兼容的可能性较小。

请始终参考与您正在使用的 Django 版本相对应的文档！

如果您执行前两个步骤中的任何一个，请留意文档中标记为**开发版本中新**内容的部分。该短语标记了仅在 Django 开发版本中可用的功能，并且它们可能不适用于正式版本。



## 验证[¶](https://docs.djangoproject.com/en/5.0/intro/install/#verifying)

要验证 Python 是否可以看到 Django，请`python`从 shell 中键入。然后在 Python 提示符下，尝试导入 Django：

```
>>> 导入 Django
>>> 打印(django.get_version())
5.0
```
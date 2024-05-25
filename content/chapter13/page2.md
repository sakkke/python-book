+++
title = "基本的なCRUDアプリケーションの作成"
weight = 14
+++

Djangoを使って基本的なCRUD（Create, Read, Update, Delete）機能を持つアプリケーションを作成します。

```python
# モデルの作成
from django.db import models

class Article(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()

# マイグレーションの作成と適用
# python manage.py makemigrations
# python manage.py migrate

# 管理サイトへのモデルの登録
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

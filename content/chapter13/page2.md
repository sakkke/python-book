+++
title = "基本的なCRUDアプリケーションの作成"
weight = 14
+++

Djangoを使って基本的なCRUD（Create, Read, Update, Delete）機能を持つアプリケーションを作成します。CRUD操作は、データベースを操作するための基本的な機能であり、ほとんどのウェブアプリケーションにおいて重要な役割を果たします。

---

### モデルの作成

まず、Djangoモデルを作成してデータベースに保存するデータの構造を定義します。以下の例では、`Article` というモデルを作成します。

```python
# myapp/models.py
from django.db import models

class Article(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()

    def __str__(self):
        return self.title
```

このモデルでは、`title` と `content` という2つのフィールドを持つ `Article` クラスを定義しています。

---

### マイグレーションの作成と適用

モデルを作成した後、マイグレーションを作成してデータベースに適用します。これにより、データベースに必要なテーブルが作成されます。

```bash
# マイグレーションの作成
python manage.py makemigrations

# マイグレーションの適用
python manage.py migrate
```

---

### 管理サイトへのモデルの登録

Django管理サイトを使って、モデルのデータを簡単に管理できるようにするため、モデルを管理サイトに登録します。

```python
# myapp/admin.py
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

これにより、管理サイトに `Article` モデルが追加され、ブラウザで管理できるようになります。

---

### ビューの作成

CRUD操作を実装するために、ビューを作成します。以下の例では、リストビュー、詳細ビュー、作成ビュー、更新ビュー、削除ビューを定義します。

```python
# myapp/views.py
from django.shortcuts import render, get_object_or_404, redirect
from .models import Article
from .forms import ArticleForm

def article_list(request):
    articles = Article.objects.all()
    return render(request, 'myapp/article_list.html', {'articles': articles})

def article_detail(request, pk):
    article = get_object_or_404(Article, pk=pk)
    return render(request, 'myapp/article_detail.html', {'article': article})

def article_create(request):
    if request.method == 'POST':
        form = ArticleForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('article_list')
    else:
        form = ArticleForm()
    return render(request, 'myapp/article_form.html', {'form': form})

def article_update(request, pk):
    article = get_object_or_404(Article, pk=pk)
    if request.method == 'POST':
        form = ArticleForm(request.POST, instance=article)
        if form.is_valid():
            form.save()
            return redirect('article_list')
    else:
        form = ArticleForm(instance=article)
    return render(request, 'myapp/article_form.html', {'form': form})

def article_delete(request, pk):
    article = get_object_or_404(Article, pk=pk)
    if request.method == 'POST':
        article.delete()
        return redirect('article_list')
    return render(request, 'myapp/article_confirm_delete.html', {'article': article})
```

---

### フォームの作成

ビューで使用するフォームを定義します。Djangoのフォームは、モデルに基づいて簡単に作成できます。

```python
# myapp/forms.py
from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = ['title', 'content']
```

---

### URLルーティングの設定

各ビューへのルーティングを設定します。これにより、特定のURLパターンに対してビューが呼び出されます。

```python
# myapp/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.article_list, name='article_list'),
    path('article/<int:pk>/', views.article_detail, name='article_detail'),
    path('article/new/', views.article_create, name='article_create'),
    path('article/<int:pk>/edit/', views.article_update, name='article_update'),
    path('article/<int:pk>/delete/', views.article_delete, name='article_delete'),
]
```

次に、プロジェクトの `urls.py` ファイルでアプリケーションのURLパターンをインクルードします。

```python
# mysite/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('myapp/', include('myapp.urls')),
]
```

---

### テンプレートの作成

最後に、ビューで使用するテンプレートを作成します。テンプレートは、HTMLファイルとして定義され、ビューから渡されたデータを表示します。

- `myapp/templates/myapp/article_list.html`:
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Article List</title>
    </head>
    <body>
        <h1>Articles</h1>
        <ul>
            {% for article in articles %}
                <li><a href="{% url 'article_detail' article.pk %}">{{ article.title }}</a></li>
            {% endfor %}
        </ul>
        <a href="{% url 'article_create' %}">Create New Article</a>
    </body>
    </html>
    ```

- `myapp/templates/myapp/article_detail.html`:
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>{{ article.title }}</title>
    </head>
    <body>
        <h1>{{ article.title }}</h1>
        <p>{{ article.content }}</p>
        <a href="{% url 'article_update' article.pk %}">Edit</a>
        <form action="{% url 'article_delete' article.pk %}" method="post">
            {% csrf_token %}
            <button type="submit">Delete</button>
        </form>
        <a href="{% url 'article_list' %}">Back to List</a>
    </body>
    </html>
    ```

- `myapp/templates/myapp/article_form.html`:
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Article Form</title>
    </head>
    <body>
        <h1>Create/Edit Article</h1>
        <form method="post">
            {% csrf_token %}
            {{ form.as_p }}
            <button type="submit">Save</button>
        </form>
        <a href="{% url 'article_list' %}">Back to List</a>
    </body>
    </html>
    ```

- `myapp/templates/myapp/article_confirm_delete.html`:
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Confirm Delete</title>
    </head>
    <body>
        <h1>Are you sure you want to delete "{{ article.title }}"?</h1>
        <form method="post">
            {% csrf_token %}
            <button type="submit">Yes, delete</button>
        </form>
        <a href="{% url 'article_list' %}">Back to List</a>
    </body>
    </html>
    ```

---

## まとめ

この章では、Djangoを使って基本的なCRUD（Create, Read, Update, Delete）機能を持つアプリケーションを作成する方法について学びました。Djangoの強力なフレームワークを活用することで、データベース操作を簡単に実装でき、迅速なウェブアプリケーション開発が可能になります。

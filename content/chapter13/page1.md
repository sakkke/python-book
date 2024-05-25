+++
title = "Djangoのインストールとセットアップ"
weight = 14
+++

Djangoは、Pythonで作られた高機能なウェブフレームワークであり、迅速なウェブアプリケーションの開発をサポートします。この章では、Djangoのインストールと基本的なセットアップ方法について学びます。

---

### Djangoのインストール

まず、Djangoをインストールします。pipを使って簡単にインストールできます。

```bash
# Djangoのインストール
pip install django
```

---

### プロジェクトの作成

Djangoプロジェクトを作成するには、`django-admin startproject` コマンドを使用します。このコマンドにより、新しいDjangoプロジェクトが作成されます。

```bash
# プロジェクトの作成
django-admin startproject mysite
```

このコマンドを実行すると、`mysite` という名前のディレクトリが作成され、その中にDjangoプロジェクトの基本構造が生成されます。

---

### プロジェクトのディレクトリ構造

プロジェクトのディレクトリ構造は以下のようになります：

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

- `manage.py`：プロジェクト管理用のスクリプト
- `settings.py`：プロジェクトの設定ファイル
- `urls.py`：URLルーティングの設定ファイル
- `wsgi.py`：WSGIコンフィギュレーション
- `asgi.py`：ASGIコンフィギュレーション

---

### 開発サーバーの起動

Djangoには、開発中に使用する簡易的な開発サーバーが組み込まれています。プロジェクトディレクトリに移動し、`runserver` コマンドを実行することで開発サーバーを起動できます。

```bash
# サーバーの起動
cd mysite
python manage.py runserver
```

このコマンドを実行すると、開発サーバーが起動し、ローカルホストの8000番ポートでウェブアプリケーションにアクセスできるようになります。ブラウザで `http://127.0.0.1:8000/` にアクセスすると、Djangoのウェルカムページが表示されます。

---

### アプリケーションの作成

Djangoプロジェクト内で個別の機能を実装するために、アプリケーションを作成します。アプリケーションはプロジェクトの中でモジュールとして扱われます。

```bash
# アプリケーションの作成
python manage.py startapp myapp
```

このコマンドを実行すると、`myapp` というディレクトリが作成され、その中に基本的なアプリケーションの構造が生成されます。

---

### アプリケーションのディレクトリ構造

アプリケーションのディレクトリ構造は以下のようになります：

```
myapp/
    __init__.py
    admin.py
    apps.py
    models.py
    tests.py
    views.py
    migrations/
```

- `admin.py`：Django管理サイトの設定ファイル
- `apps.py`：アプリケーションの設定ファイル
- `models.py`：データベースモデルの定義ファイル
- `tests.py`：ユニットテストの定義ファイル
- `views.py`：ビューの定義ファイル
- `migrations/`：データベースマイグレーションの管理ディレクトリ

---

### アプリケーションの設定

作成したアプリケーションをプロジェクトに追加するには、プロジェクトの `settings.py` ファイルを編集し、`INSTALLED_APPS` にアプリケーションを追加します。

```python
# settings.py

INSTALLED_APPS = [
    ...
    'myapp',
]
```

---

### URLルーティングの設定

アプリケーションのビューを表示するために、プロジェクトの `urls.py` ファイルを編集し、アプリケーションのURLルーティングを設定します。

```python
# mysite/urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('myapp/', include('myapp.urls')),
]
```

次に、アプリケーションの `urls.py` ファイルを作成し、ビューのルーティングを定義します。

```python
# myapp/urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

---

### ビューの作成

アプリケーションの `views.py` ファイルにビューを定義します。ビューは、HTTPリクエストを受け取り、HTTPレスポンスを返す関数やクラスです。

```python
# myapp/views.py

from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world!")
```

---

### アプリケーションの動作確認

開発サーバーを再起動し、ブラウザで `http://127.0.0.1:8000/myapp/` にアクセスすると、`"Hello, world!"` というメッセージが表示されます。

---

## まとめ

この章では、Djangoのインストールと基本的なセットアップ方法について学びました。Djangoを使うことで、高機能なウェブアプリケーションを迅速に構築することができます。次の章では、基本的なCRUD（Create, Read, Update, Delete）操作を行うためのDjangoモデルとフォームについて学びます。これにより、データベースと連携したウェブアプリケーションの作成が可能になります。

+++
title = "Scrapyの紹介"
weight = 13
+++

Scrapyは、高度なウェブスクレイピングとウェブクローリングのためのフレームワークです。効率的かつスケーラブルなウェブデータの収集を可能にし、複雑なスクレイピング作業を簡単に行うことができます。この章では、Scrapyの基本的な使い方について学びます。

---

### Scrapyのインストール

Scrapyを使用するには、まずパッケージをインストールします。pipを使用して簡単にインストールできます。

```bash
# Scrapyのインストール
pip install scrapy
```

---

### Scrapyプロジェクトの開始

Scrapyでは、スクレイピングプロジェクトを管理するためにプロジェクトを作成します。以下のコマンドを使用して新しいプロジェクトを開始します。

```bash
# Scrapyプロジェクトの開始
scrapy startproject example
```

このコマンドを実行すると、`example` という名前のディレクトリが作成され、その中にScrapyプロジェクトの基本構造が生成されます。

---

### Scrapyスパイダーの作成

Scrapyでは、スパイダーと呼ばれるクラスを作成して、特定のウェブサイトからデータを収集します。スパイダーを作成するには、以下のコマンドを使用します。

```bash
# Scrapyスパイダーの作成
scrapy genspider example_spider example.com
```

このコマンドを実行すると、`example/spiders` ディレクトリ内に `example_spider.py` ファイルが作成されます。このファイルにスパイダーの設定を記述します。

---

### スパイダーの基本構造

スパイダーの基本構造は以下のようになります。`start_requests` メソッドでクローリングを開始し、`parse` メソッドでデータを解析します。

```python
import scrapy

class ExampleSpider(scrapy.Spider):
    name = "example_spider"
    allowed_domains = ["example.com"]
    start_urls = ["http://example.com"]

    def parse(self, response):
        self.log(f"Visited {response.url}")
```

---

### データの抽出

Scrapyでは、XPathやCSSセレクタを使ってHTMLからデータを抽出します。以下は、タイトルとリンクを抽出する例です。

```python
import scrapy

class ExampleSpider(scrapy.Spider):
    name = "example_spider"
    allowed_domains = ["example.com"]
    start_urls = ["http://example.com"]

    def parse(self, response):
        for title in response.xpath("//h1/text()").getall():
            yield {"title": title}

        for link in response.css("a::attr(href)").getall():
            yield {"link": link}
```

---

### アイテムの使用

Scrapyでは、抽出したデータをアイテム（Item）として管理します。アイテムを定義するには、`items.py` ファイルを編集します。

```python
# items.py
import scrapy

class ExampleItem(scrapy.Item):
    title = scrapy.Field()
    link = scrapy.Field()
```

スパイダーでアイテムを使用するには、以下のようにします。

```python
import scrapy
from example.items import ExampleItem

class ExampleSpider(scrapy.Spider):
    name = "example_spider"
    allowed_domains = ["example.com"]
    start_urls = ["http://example.com"]

    def parse(self, response):
        item = ExampleItem()
        item["title"] = response.xpath("//h1/text()").get()
        item["link"] = response.css("a::attr(href)").get()
        yield item
```

---

### データの保存

Scrapyは、抽出したデータを様々な形式で保存することができます。デフォルトでは、`scrapy crawl` コマンドにオプションを追加することで、JSONやCSV形式で保存できます。

```bash
# データをJSON形式で保存
scrapy crawl example_spider -o output.json

# データをCSV形式で保存
scrapy crawl example_spider -o output.csv
```

---

### 高度な設定

Scrapyは、クローリングの動作を細かく制御するための高度な設定オプションを提供しています。これらの設定は、`settings.py` ファイルで行います。例えば、クローリングの速度を制御するための設定や、ユーザーエージェントを指定する設定があります。

```python
# settings.py
# クローリングの間隔を設定（デフォルトは0）
DOWNLOAD_DELAY = 1.0

# ユーザーエージェントを設定
USER_AGENT = "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36"
```

---

### ミドルウェアの使用

Scrapyは、リクエストやレスポンスの処理をカスタマイズするためのミドルウェアをサポートしています。これにより、プロキシの設定やカスタムヘッダーの追加などが可能です。

```python
# ミドルウェアの設定
DOWNLOADER_MIDDLEWARES = {
    'myproject.middlewares.CustomMiddleware': 543,
}

# カスタムミドルウェアの定義
class CustomMiddleware:
    def process_request(self, request, spider):
        request.headers["X-Custom-Header"] = "CustomValue"
        return None
```

---

## まとめ

この章では、Scrapyを使ったウェブスクレイピングの基本的な使い方について学びました。Scrapyは、高度なウェブクローリングとスクレイピングのための強力なフレームワークであり、大量のデータを効率的に収集するのに適しています。次の章では、Djangoを使ったウェブ開発について学びます。Djangoは、高機能なウェブアプリケーションを迅速に構築するためのフレームワークです。

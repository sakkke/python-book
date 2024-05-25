+++
title = "BeautifulSoupの使い方"
weight = 13
+++

BeautifulSoupは、HTMLやXMLファイルを解析し、データを抽出するための強力なライブラリです。ウェブスクレイピングに広く使用されており、ウェブページから特定の情報を取得するために使用されます。この章では、BeautifulSoupの基本的な使い方について学びます。

---

### BeautifulSoupのインポート

まず、BeautifulSoupライブラリとrequestsライブラリをインポートします。requestsライブラリは、ウェブページの取得に使用します。

```python
from bs4 import BeautifulSoup
import requests
```

---

### ウェブページの取得

requestsライブラリを使って、解析するウェブページを取得します。

```python
# ウェブページの取得
url = "http://example.com"
response = requests.get(url)
```

---

### BeautifulSoupによる解析

取得したウェブページの内容をBeautifulSoupで解析します。解析の方法として、`html.parser` を指定します。

```python
# BeautifulSoupによる解析
soup = BeautifulSoup(response.content, "html.parser")
```

---

### タイトルの取得

解析したHTMLから特定の要素を抽出します。例えば、ページのタイトルを取得するには、`title` タグを使います。

```python
# タイトルの取得
title = soup.title.string
print(title)  # 出力: Example Domain
```

---

### 特定のタグを取得

特定のタグを取得するために、`find` や `find_all` メソッドを使用します。

```python
# 特定のタグの取得
h1_tag = soup.find("h1")
print(h1_tag.text)  # 出力: Example Domain

# すべてのリンクを取得
links = soup.find_all("a")
for link in links:
    print(link.get("href"))
```

---

### 属性でフィルタリング

タグの属性でフィルタリングして、特定の要素を取得することができます。

```python
# id属性を使ってフィルタリング
div_with_id = soup.find("div", id="specific-id")
print(div_with_id)

# class属性を使ってフィルタリング
divs_with_class = soup.find_all("div", class_="specific-class")
for div in divs_with_class:
    print(div)
```

---

### ネストされたタグの取得

BeautifulSoupを使って、ネストされたタグを簡単に取得できます。

```python
# ネストされたタグの取得
nested_div = soup.find("div", {"class": "outer-div"}).find("div", {"class": "inner-div"})
print(nested_div)
```

---

### 親タグ、子タグ、兄弟タグの取得

BeautifulSoupでは、親タグ、子タグ、兄弟タグにアクセスすることもできます。

```python
# 親タグの取得
parent = soup.find("div", {"class": "child-div"}).parent
print(parent)

# 子タグの取得
children = soup.find("div", {"class": "parent-div"}).children
for child in children:
    print(child)

# 兄弟タグの取得
sibling = soup.find("div", {"class": "sibling-div"}).find_next_sibling("div")
print(sibling)
```

---

### データの抽出と保存

抽出したデータをファイルに保存することも簡単にできます。

```python
# リンクのリストを取得
links = soup.find_all("a")

# リンクをファイルに保存
with open("links.txt", "w") as file:
    for link in links:
        file.write(link.get("href") + "\n")
```

---

### BeautifulSoupの応用例

BeautifulSoupを使って、ニュースサイトから記事のタイトルとリンクを取得する例を示します。

```python
# ニュースサイトのURL
url = "https://news.ycombinator.com/"
response = requests.get(url)
soup = BeautifulSoup(response.content, "html.parser")

# 記事のタイトルとリンクを取得
articles = soup.find_all("a", class_="storylink")
for article in articles:
    title = article.text
    link = article.get("href")
    print(f"Title: {title}\nLink: {link}\n")
```

この例では、Hacker Newsサイトから記事のタイトルとリンクを取得しています。

---

## まとめ

この章では、BeautifulSoupを使ったウェブスクレイピングの基本的な使い方について学びました。BeautifulSoupを使うことで、HTMLやXMLファイルを解析し、特定のデータを抽出することができます。次の章では、Scrapyについて学びます。Scrapyは、より高度なウェブスクレイピングを行うための強力なフレームワークです。

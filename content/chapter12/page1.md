+++
title = "BeautifulSoupの使い方"
weight = 13
+++

BeautifulSoupは、HTMLやXMLファイルを解析し、データを抽出するためのライブラリです。

```python
from bs4 import BeautifulSoup
import requests

# ウェブページの取得
url = "http://example.com"
response = requests.get(url)

# BeautifulSoupによる解析
soup = BeautifulSoup(response.content, "html.parser")

# タイトルの取得
title = soup.title.string
print(title)
```

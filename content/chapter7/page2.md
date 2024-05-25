+++
title = "標準ライブラリの紹介"
weight = 8
+++

Pythonの標準ライブラリには、多くの便利なモジュールが含まれています。以下はその一部です。

- **os**: OS関連の機能
- **sys**: システム関連の機能
- **datetime**: 日付と時刻の操作
- **random**: 擬似乱数生成

```python
import os
import sys
import datetime
import random

# カレントディレクトリの取得
print(os.getcwd())
# コマンドライン引数の取得
print(sys.argv)
# 現在の日付と時刻の取得
print(datetime.datetime.now())
# 乱数の生成
print(random.randint(1, 10))
```

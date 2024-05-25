+++
title = "標準ライブラリの紹介"
weight = 8
+++

Pythonの標準ライブラリには、多くの便利なモジュールが含まれています。これらのモジュールを使用することで、様々なタスクを簡単に実行することができます。この章では、いくつかの主要な標準ライブラリについて紹介します。

---

### os モジュール

`os` モジュールは、OS（オペレーティングシステム）関連の機能を提供します。ファイルやディレクトリの操作、環境変数の取得などが可能です。

```python
import os

# カレントディレクトリの取得
current_directory = os.getcwd()
print(current_directory)  # 出力: 現在の作業ディレクトリ

# ディレクトリの作成
os.mkdir('new_directory')

# ファイルの削除
os.remove('sample.txt')

# 環境変数の取得
path = os.getenv('PATH')
print(path)
```

---

### sys モジュール

`sys` モジュールは、システム関連の機能を提供します。Pythonインタプリタに関する情報やコマンドライン引数の取得が可能です。

```python
import sys

# コマンドライン引数の取得
arguments = sys.argv
print(arguments)  # 出力: コマンドライン引数のリスト

# Pythonのバージョン情報
version = sys.version
print(version)
```

---

### datetime モジュール

`datetime` モジュールは、日付と時刻の操作に使用します。現在の日付と時刻の取得、特定の日付の作成、日付の差分計算などが可能です。

```python
import datetime

# 現在の日付と時刻の取得
now = datetime.datetime.now()
print(now)  # 出力: 現在の日付と時刻

# 特定の日付の作成
birthday = datetime.date(1990, 1, 1)
print(birthday)  # 出力: 1990-01-01

# 日付の差分計算
delta = datetime.timedelta(days=100)
future_date = now + delta
print(future_date)  # 出力: 100日後の日付
```

---

### random モジュール

`random` モジュールは、擬似乱数を生成するために使用します。ランダムな整数、浮動小数点数、シーケンスからのランダムな選択などが可能です。

```python
import random

# 1から10までのランダムな整数を生成
rand_int = random.randint(1, 10)
print(rand_int)

# 0から1までのランダムな浮動小数点数を生成
rand_float = random.random()
print(rand_float)

# リストからランダムな要素を選択
choices = ['apple', 'banana', 'cherry']
rand_choice = random.choice(choices)
print(rand_choice)
```

---

### collections モジュール

`collections` モジュールは、高度なデータ構造を提供します。`namedtuple`、`deque`、`Counter` などがあります。

```python
import collections

# namedtupleの使用
Point = collections.namedtuple('Point', ['x', 'y'])
p = Point(10, 20)
print(p.x, p.y)  # 出力: 10 20

# dequeの使用
d = collections.deque([1, 2, 3])
d.append(4)
d.appendleft(0)
print(d)  # 出力: deque([0, 1, 2, 3, 4])

# Counterの使用
counter = collections.Counter('abracadabra')
print(counter)  # 出力: Counter({'a': 5, 'b': 2, 'r': 2, 'c': 1, 'd': 1})
```

---

### itertools モジュール

`itertools` モジュールは、イテレータ生成のための関数を提供します。無限イテレータ、組み合わせ、順列などがあります。

```python
import itertools

# 無限カウント
for i in itertools.count(10):
    if i > 15:
        break
    print(i)  # 出力: 10 11 12 13 14 15

# 順列
permutations = itertools.permutations([1, 2, 3])
for p in permutations:
    print(p)  # 出力: (1, 2, 3) (1, 3, 2) (2, 1, 3) (2, 3, 1) (3, 1, 2) (3, 2, 1)
```

---

### json モジュール

`json` モジュールは、JSONデータのエンコードとデコードを行います。PythonオブジェクトとJSON形式の文字列の相互変換が可能です。

```python
import json

# PythonオブジェクトをJSON文字列に変換
data = {'name': 'Alice', 'age': 25, 'city': 'New York'}
json_str = json.dumps(data)
print(json_str)  # 出力: {"name": "Alice", "age": 25, "city": "New York"}

# JSON文字列をPythonオブジェクトに変換
json_data = '{"name": "Bob", "age": 30, "city": "Los Angeles"}'
python_obj = json.loads(json_data)
print(python_obj)  # 出力: {'name': 'Bob', 'age': 30, 'city': 'Los Angeles'}
```

---

## まとめ

この章では、Pythonの標準ライブラリの一部を紹介しました。標準ライブラリを利用することで、多くの機能を簡単に実装することができます。次の章では、外部パッケージのインストールと使用方法について学びます。これにより、標準ライブラリでは提供されない追加の機能を簡単に取り入れることができます。

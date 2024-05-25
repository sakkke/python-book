+++
title = "JSONファイルの操作"
weight = 9
+++

JSON（JavaScript Object Notation）は、データを構造化して保存するための軽量なフォーマットです。Pythonの `json` モジュールを使うことで、JSONファイルの読み書きを簡単に行うことができます。この章では、JSONファイルの基本的な操作方法について学びます。

---

### JSONファイルの書き込み

PythonのオブジェクトをJSON形式でファイルに書き込むには、`json.dump` メソッドを使用します。次の例では、辞書オブジェクトをJSONファイルに書き込みます。

```python
import json

# 書き込むデータ
data = {"name": "Alice", "age": 25, "city": "New York"}

# JSONファイルの書き込み
with open("example.json", "w") as file:
    json.dump(data, file)
```

この例では、`example.json` というファイルに辞書 `data` の内容をJSON形式で書き込んでいます。

---

### JSONファイルの読み込み

JSONファイルからデータを読み込むには、`json.load` メソッドを使用します。次の例では、JSONファイルからデータを読み込んで辞書オブジェクトとして取得します。

```python
import json

# JSONファイルの読み込み
with open("example.json", "r") as file:
    data = json.load(file)
    print(data)
```

この例では、`example.json` というファイルからJSONデータを読み込み、辞書 `data` として表示しています。

---

### JSON文字列の操作

`json` モジュールを使うと、PythonオブジェクトをJSON形式の文字列に変換したり、その逆を行ったりすることもできます。

#### PythonオブジェクトをJSON文字列に変換

```python
import json

# Pythonオブジェクト
data = {"name": "Alice", "age": 25, "city": "New York"}

# JSON文字列に変換
json_str = json.dumps(data)
print(json_str)  # 出力: {"name": "Alice", "age": 25, "city": "New York"}
```

#### JSON文字列をPythonオブジェクトに変換

```python
import json

# JSON文字列
json_str = '{"name": "Alice", "age": 25, "city": "New York"}'

# Pythonオブジェクトに変換
data = json.loads(json_str)
print(data)  # 出力: {'name': 'Alice', 'age': 25, 'city': 'New York'}
```

---

### JSONファイルの高度な操作

`json.dump` および `json.dumps` メソッドには、出力をカスタマイズするためのオプションがいくつかあります。

#### インデントを使った整形

JSONファイルを読みやすい形式で保存するために、インデントを指定することができます。

```python
import json

# 書き込むデータ
data = {"name": "Alice", "age": 25, "city": "New York"}

# JSONファイルの書き込み（インデント付き）
with open("example_pretty.json", "w") as file:
    json.dump(data, file, indent=4)
```

この例では、インデントを指定してJSONデータを整形して書き込んでいます。

#### ソートされたキー

JSONデータをキーでソートして出力することもできます。

```python
import json

# 書き込むデータ
data = {"name": "Alice", "age": 25, "city": "New York"}

# JSONファイルの書き込み（キーでソート）
with open("example_sorted.json", "w") as file:
    json.dump(data, file, sort_keys=True, indent=4)
```

この例では、キーでソートされた状態でJSONデータをファイルに書き込んでいます。

---

### 辞書をJSON形式でファイルに保存する関数

ファイル操作を行うコードを再利用しやすくするために、辞書をJSON形式でファイルに保存する関数を作成できます。

```python
import json

def save_to_json(data, filename):
    with open(filename, "w") as file:
        json.dump(data, file, indent=4)

data = {"name": "Alice", "age": 25, "city": "New York"}
save_to_json(data, "example_function.json")
```

この例では、`save_to_json` 関数を使って辞書データをファイルに保存しています。

---

### JSONファイルから辞書を読み込む関数

同様に、JSONファイルから辞書を読み込む関数も作成できます。

```python
import json

def load_from_json(filename):
    with open(filename, "r") as file:
        return json.load(file)

data = load_from_json("example_function.json")
print(data)
```

この例では、`load_from_json` 関数を使ってファイルから辞書データを読み込んでいます。

---

## まとめ

この章では、PythonでのJSONファイルの操作について学びました。`json` モジュールを使うことで、JSONファイルの読み書きを簡単に行うことができます。次の章では、エラー処理について学びます。エラー処理を理解することで、プログラムの信頼性と安定性を向上させることができます。

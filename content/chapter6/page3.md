+++
title = "辞書"
weight = 7
+++

辞書（dictionary）は、キーと値のペアを保持するデータ構造です。キーは一意でなければならず、値は任意のデータ型を取ることができます。辞書は、キーによる高速なデータアクセスが可能であり、データを効率的に管理するのに適しています。

---

### 辞書の作成

辞書は波括弧 `{}` を使って作成し、キーと値のペアをコロン `:` で区切ります。

```python
# 辞書の作成
person = {"name": "Alice", "age": 25}
```

---

### 要素へのアクセス

辞書の要素には、キーを使ってアクセスします。キーを指定して対応する値を取得します。

```python
# 要素へのアクセス
print(person["name"])  # 出力: Alice
print(person["age"])   # 出力: 25
```

---

### 要素の追加と更新

辞書に新しい要素を追加するには、既存のキーに新しい値を割り当てます。既存のキーに対して値を割り当てると、その値が更新されます。

```python
# 要素の追加
person["city"] = "New York"
print(person)  # 出力: {'name': 'Alice', 'age': 25, 'city': 'New York'}

# 要素の更新
person["age"] = 26
print(person)  # 出力: {'name': 'Alice', 'age': 26, 'city': 'New York'}
```

---

### 要素の削除

辞書から要素を削除する方法はいくつかあります：

- `del` キーワードを使ってキーと値のペアを削除する。
- `pop` メソッドを使ってキーと値のペアを削除し、その値を取得する。

```python
# 要素の削除（del）
del person["age"]
print(person)  # 出力: {'name': 'Alice', 'city': 'New York'}

# 要素の削除（pop）
city = person.pop("city")
print(city)    # 出力: New York
print(person)  # 出力: {'name': 'Alice'}
```

---

### 辞書のメソッド

辞書には便利なメソッドがいくつかあります。

- `keys()`：辞書のすべてのキーを返す。
- `values()`：辞書のすべての値を返す。
- `items()`：辞書のすべてのキーと値のペアを返す。
- `get()`：キーを指定して値を取得する。キーが存在しない場合にデフォルト値を返す。

```python
# 辞書のメソッドの例
person = {"name": "Alice", "age": 25, "city": "New York"}

# すべてのキーを取得
keys = person.keys()
print(keys)  # 出力: dict_keys(['name', 'age', 'city'])

# すべての値を取得
values = person.values()
print(values)  # 出力: dict_values(['Alice', 25, 'New York'])

# すべてのキーと値のペアを取得
items = person.items()
print(items)  # 出力: dict_items([('name', 'Alice'), ('age', 25), ('city', 'New York')])

# キーを指定して値を取得
name = person.get("name")
print(name)  # 出力: Alice

# 存在しないキーを指定した場合のデフォルト値
country = person.get("country", "USA")
print(country)  # 出力: USA
```

---

### 辞書のイテレーション

辞書はループで繰り返し処理することができます。`items()` メソッドを使うと、キーと値の両方にアクセスできます。

```python
# 辞書のイテレーション
person = {"name": "Alice", "age": 25, "city": "New York"}
for key, value in person.items():
    print(f"{key}: {value}")
# 出力:
# name: Alice
# age: 25
# city: New York
```

---

### ネストされた辞書

辞書は他の辞書を値として含むことができます。これをネストされた辞書と呼びます。

```python
# ネストされた辞書の例
students = {
    "Alice": {"age": 25, "city": "New York"},
    "Bob": {"age": 30, "city": "Los Angeles"},
    "Charlie": {"age": 22, "city": "Chicago"}
}

print(students["Alice"]["city"])  # 出力: New York
```

---

### 辞書の用途

辞書は以下のような用途に適しています：

1. **データの関連付け**：キーと値のペアでデータを関連付けるため、特定のキーに対してすぐに値を見つけることができます。
2. **データベースのような操作**：辞書はデータベースのレコードのように扱うことができ、データの追加、更新、削除が容易です。
3. **設定管理**：プログラムの設定やオプションを管理するために辞書を使うことがよくあります。

---

## まとめ

この章では、Pythonの辞書について学びました。辞書はキーと値のペアを保持するデータ構造であり、データの高速な検索と操作が可能です。次の章では、集合（セット）について学びます。集合は一意の要素を保持するデータ構造で、重複を排除するのに役立ちます。

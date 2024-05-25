+++
title = "集合"
weight = 7
+++

集合（set）は、一意の要素を保持するデータ構造です。順序は保証されず、重複する要素は含まれません。集合は数学の集合と同様に、和集合、積集合、差集合などの操作が可能です。この章では、集合の作成、操作、便利なメソッドについて学びます。

---

### 集合の作成

集合は波括弧 `{}` を使って作成します。集合内の要素はカンマで区切ります。

```python
# 集合の作成
fruits = {"apple", "banana", "cherry"}
print(fruits)  # 出力: {'apple', 'banana', 'cherry'}
```

また、`set()` 関数を使って集合を作成することもできます。

```python
# set() 関数を使って集合を作成
numbers = set([1, 2, 3, 4, 5])
print(numbers)  # 出力: {1, 2, 3, 4, 5}
```

---

### 要素の追加

集合には `add` メソッドを使って要素を追加できます。

```python
# 要素の追加
fruits.add("date")
print(fruits)  # 出力: {'apple', 'banana', 'cherry', 'date'}
```

---

### 要素の削除

集合から要素を削除する方法はいくつかあります。

- `remove` メソッドを使って指定した要素を削除する（存在しない要素を削除しようとするとエラーが発生する）。
- `discard` メソッドを使って指定した要素を削除する（存在しない要素を削除しようとしてもエラーは発生しない）。
- `pop` メソッドを使ってランダムな要素を削除し、その値を返す。
- `clear` メソッドを使ってすべての要素を削除する。

```python
# 要素の削除（remove）
fruits.remove("banana")
print(fruits)  # 出力: {'apple', 'cherry', 'date'}

# 要素の削除（discard）
fruits.discard("cherry")
print(fruits)  # 出力: {'apple', 'date'}

# 要素の削除（pop）
removed_element = fruits.pop()
print(removed_element)  # 出力: 'apple'（削除された要素）
print(fruits)  # 出力: {'date'}

# すべての要素を削除（clear）
fruits.clear()
print(fruits)  # 出力: set()
```

---

### 集合の長さ

集合の長さ（要素の数）は、`len` 関数を使って取得できます。

```python
# 集合の長さ
fruits = {"apple", "banana", "cherry"}
print(len(fruits))  # 出力: 3
```

---

### 集合の操作

集合は数学の集合と同様に、和集合、積集合、差集合などの操作が可能です。

- **和集合**（union）：二つの集合のすべての要素を含む新しい集合を返す。
- **積集合**（intersection）：二つの集合に共通する要素を含む新しい集合を返す。
- **差集合**（difference）：一方の集合にのみ含まれる要素を含む新しい集合を返す。
- **対称差集合**（symmetric_difference）：二つの集合のどちらか一方にのみ含まれる要素を含む新しい集合を返す。

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# 和集合
union_set = set1.union(set2)
print(union_set)  # 出力: {1, 2, 3, 4, 5}

# 積集合
intersection_set = set1.intersection(set2)
print(intersection_set)  # 出力: {3}

# 差集合
difference_set = set1.difference(set2)
print(difference_set)  # 出力: {1, 2}

# 対称差集合
symmetric_difference_set = set1.symmetric_difference(set2)
print(symmetric_difference_set)  # 出力: {1, 2, 4, 5}
```

---

### 集合のメソッド

集合には便利なメソッドがいくつかあります。

- `isdisjoint`：二つの集合が共通の要素を持たない場合に `True` を返す。
- `issubset`：ある集合が他の集合の部分集合である場合に `True` を返す。
- `issuperset`：ある集合が他の集合を包含する場合に `True` を返す。

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
set3 = {1, 2}

# 共通の要素がないか確認
print(set1.isdisjoint(set2))  # 出力: False

# 部分集合かどうか確認
print(set3.issubset(set1))  # 出力: True

# 包含しているかどうか確認
print(set1.issuperset(set3))  # 出力: True
```

---

### 集合のイテレーション

集合はループで繰り返し処理することができます。

```python
fruits = {"apple", "banana", "cherry"}
for fruit in fruits:
    print(fruit)
# 出力:
# apple
# banana
# cherry
```

---

## まとめ

この章では、Pythonの集合について学びました。集合は一意の要素を保持するデータ構造であり、重複を排除し、数学的な集合演算をサポートします。次の章では、モジュールとパッケージについて学びます。モジュールとパッケージを使うことで、コードを整理し再利用することができます。

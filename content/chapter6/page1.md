+++
title = "リスト"
weight = 7
+++

リストは、複数の値を順序付きで保持するデータ構造で、Pythonにおける最も基本的かつ重要なデータ型の一つです。リストは変更可能（ミュータブル）であり、異なるデータ型の要素を含むことができます。この章では、リストの作成、操作、便利なメソッドについて学びます。

---

### リストの作成

リストは角括弧 `[]` を使って作成します。リストの要素はカンマで区切ります。

```python
# リストの作成
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
mixed = [1, "apple", 3.14, True]
```

---

### 要素へのアクセス

リストの要素には、インデックスを使ってアクセスできます。インデックスは0から始まります。

```python
# 要素へのアクセス
print(fruits[0])  # 出力: apple
print(fruits[1])  # 出力: banana
print(fruits[2])  # 出力: cherry
```

負のインデックスを使うと、リストの末尾から要素にアクセスできます。

```python
print(fruits[-1])  # 出力: cherry
print(fruits[-2])  # 出力: banana
```

---

### 要素の追加

リストには `append` メソッドを使って要素を追加できます。

```python
# 要素の追加
fruits.append("date")
print(fruits)  # 出力: ['apple', 'banana', 'cherry', 'date']
```

---

### 要素の挿入

`insert` メソッドを使うと、指定した位置に要素を挿入できます。

```python
# 要素の挿入
fruits.insert(1, "blueberry")
print(fruits)  # 出力: ['apple', 'blueberry', 'banana', 'cherry', 'date']
```

---

### 要素の削除

リストから要素を削除する方法はいくつかあります。

- `remove` メソッドを使って、指定した値の最初の出現を削除する。
- `pop` メソッドを使って、指定したインデックスの要素を削除する（インデックスを指定しなければ末尾の要素を削除する）。
- `del` キーワードを使って、指定したインデックスの要素を削除する。

```python
# 要素の削除（値を指定）
fruits.remove("banana")
print(fruits)  # 出力: ['apple', 'blueberry', 'cherry', 'date']

# 要素の削除（インデックスを指定）
fruits.pop(1)
print(fruits)  # 出力: ['apple', 'cherry', 'date']

# 要素の削除（インデックスを指定）
del fruits[0]
print(fruits)  # 出力: ['cherry', 'date']
```

---

### リストの長さ

リストの長さ（要素の数）は、`len` 関数を使って取得できます。

```python
print(len(fruits))  # 出力: 2
```

---

### リストのスライス

リストの一部を取得するには、スライス構文を使います。スライス構文は `リスト[開始:終了:ステップ]` の形式で指定します。

```python
# リストのスライス
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers[2:5])  # 出力: [2, 3, 4]
print(numbers[:5])   # 出力: [0, 1, 2, 3, 4]
print(numbers[5:])   # 出力: [5, 6, 7, 8, 9]
print(numbers[::2])  # 出力: [0, 2, 4, 6, 8]
print(numbers[::-1]) # 出力: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

---

### リストの結合と複製

リストを結合するには `+` 演算子を使い、リストを複製するには `*` 演算子を使います。

```python
# リストの結合
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined = list1 + list2
print(combined)  # 出力: [1, 2, 3, 4, 5, 6]

# リストの複製
repeated = list1 * 3
print(repeated)  # 出力: [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

---

### リスト内包表記

リスト内包表記を使うと、リストの生成を簡潔に記述できます。

```python
# リスト内包表記の例
squares = [x**2 for x in range(10)]
print(squares)  # 出力: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

---

## まとめ

この章では、Pythonのリストについて学びました。リストは、複数の値を順序付きで保持するデータ構造で、要素の追加、削除、アクセス、スライスなどの操作が可能です。次の章では、タプルについて学びます。タプルはリストと似ていますが、変更不可能なデータ構造です。

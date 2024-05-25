+++
title = "繰り返し処理（for文、while文）"
weight = 5
+++

繰り返し処理を使うことで、同じ処理を複数回実行することができます。Pythonには、主に `for` 文と `while` 文の二つの繰り返し処理があります。これらを使うことで、コードの効率性を高めることができます。

---

### for文

`for` 文は、リストやタプル、文字列などのイテラブルオブジェクトを順に処理するために使います。基本的な構文は以下の通りです：

```python
for 要素 in イテラブルオブジェクト:
    実行するコード
```

例：

```python
# 0から4までの数値を順に出力
for i in range(5):
    print(i)
```

`range` 関数は、指定した範囲の数値を生成するイテラブルオブジェクトを返します。`range(5)` は 0 から 4 までの数値を生成します。

---

#### リストを使ったfor文の例

```python
# リスト内の要素を順に出力
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

---

#### ネストされたfor文

for文の中にさらにfor文を入れることもできます。これをネストされたfor文と呼びます。

例：

```python
# 二重ループの例
for i in range(3):
    for j in range(2):
        print(f"i={i}, j={j}")
```

---

### while文

`while` 文は、指定された条件が `True` である限り、繰り返し処理を行います。基本的な構文は以下の通りです：

```python
while 条件:
    実行するコード
```

例：

```python
# 0から4までの数値を順に出力
count = 0
while count < 5:
    print(count)
    count += 1
```

---

#### 無限ループ

`while` 文は条件が `True` である限り無限に実行され続けます。無限ループを避けるために、条件を適切に設定し、ループ内で条件が `False` になるようにする必要があります。

例：

```python
# 無限ループの例
while True:
    print("無限ループです")
    break  # ループを終了するためにbreak文を使用
```

---

### break文とcontinue文

`break` 文は、ループを途中で終了するために使用します。`continue` 文は、ループの残りの部分をスキップし、次の反復に進むために使用します。

例：

```python
# break文の例
for i in range(10):
    if i == 5:
        break  # iが5になったらループを終了
    print(i)

# continue文の例
for i in range(10):
    if i % 2 == 0:
        continue  # iが偶数の場合は残りの処理をスキップ
    print(i)
```

---

### ループとelse文

Pythonでは、ループが正常に終了した場合に実行される `else` 文を使うことができます。`for` または `while` ループが `break` によって終了しなかった場合にのみ実行されます。

例：

```python
# ループが正常終了した場合のelse文の例
for i in range(5):
    print(i)
else:
    print("ループが正常に終了しました")

# breakによって終了した場合はelse文は実行されない
for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("このメッセージは表示されません")
```

---

## まとめ

この章では、Pythonの繰り返し処理について学びました。`for` 文と `while` 文を使うことで、特定の条件を満たす限り同じ処理を繰り返し実行することができます。次の章では、関数の定義と使用方法について学びます。関数を使うことで、コードの再利用性を高め、プログラムをより整理された形で書くことができます。

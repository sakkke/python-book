+++
title = "関数の定義と呼び出し"
weight = 6
+++

関数を使うことで、コードを再利用しやすくなり、読みやすさも向上します。関数は一連のステートメントをまとめて名前を付けたものです。Pythonでは `def` キーワードを使って関数を定義します。

---

### 基本的な関数の定義と呼び出し

関数を定義するためには、`def` キーワードの後に関数名、引数リスト（括弧で囲む）、そしてコロン（:）を続けて、関数の内容をインデントして記述します。

```python
def greet(name):
    return f"Hello, {name}!"

# 関数の呼び出し
print(greet("Alice"))  # 出力: Hello, Alice!
```

---

### 複数の引数を持つ関数

関数は複数の引数を受け取ることができます。引数はカンマで区切って定義します。

```python
def add(a, b):
    return a + b

print(add(3, 5))  # 出力: 8
```

---

### デフォルト引数

関数の引数にはデフォルト値を設定することができます。デフォルト値を設定することで、引数が省略された場合にその値が使われます。

```python
def greet(name, message="Hello"):
    return f"{message}, {name}!"

print(greet("Bob"))           # 出力: Hello, Bob!
print(greet("Carol", "Hi"))   # 出力: Hi, Carol!
```

---

### キーワード引数

関数を呼び出す際に、引数名を指定して値を渡すことができます。これをキーワード引数と呼びます。

```python
def greet(name, message="Hello"):
    return f"{message}, {name}!"

print(greet(name="Dave", message="Good morning"))  # 出力: Good morning, Dave!
```

---

### 可変長引数

関数が可変長の引数を受け取ることができるようにするには、引数の前に `*` を付けます。これにより、任意の数の引数をタプルとして受け取ることができます。

```python
def sum_all(*numbers):
    return sum(numbers)

print(sum_all(1, 2, 3, 4, 5))  # 出力: 15
```

---

### 可変長キーワード引数

関数が可変長のキーワード引数を受け取ることができるようにするには、引数の前に `**` を付けます。これにより、任意の数のキーワード引数を辞書として受け取ることができます。

```python
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

print_info(name="Eve", age=25, country="Japan")
# 出力:
# name: Eve
# age: 25
# country: Japan
```

---

### 関数のドキュメント文字列（docstring）

関数の説明を記述するために、関数の定義直後にドキュメント文字列（docstring）を使うことができます。ドキュメント文字列はトリプルクオートで囲まれた文字列で、関数の用途や動作を説明します。

```python
def greet(name):
    """
    この関数は、指定された名前に対して挨拶を返します。
    
    Parameters:
    name (str): 挨拶する相手の名前

    Returns:
    str: 挨拶のメッセージ
    """
    return f"Hello, {name}!"

print(greet.__doc__)
```

---

### 関数のスコープとローカル変数

関数内で定義された変数は、その関数内でのみ有効なローカル変数です。関数外で定義された変数とは別のものとして扱われます。

```python
def my_function():
    local_var = "I am local"
    print(local_var)

my_function()  # 出力: I am local
# print(local_var)  # エラー: NameError: name 'local_var' is not defined
```

---

### 再帰関数

再帰関数は、自分自身を呼び出す関数です。再帰関数は、問題を小さな部分に分割して解決するのに便利です。

例：階乗を計算する再帰関数

```python
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # 出力: 120
```

---

## まとめ

この章では、Pythonの関数について学びました。関数を使うことで、コードを再利用しやすくなり、プログラムの可読性が向上します。次の章では、データ構造について学びます。データ構造を理解することで、データの効率的な操作が可能になります。

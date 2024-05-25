+++
title = "引数と戻り値"
weight = 6
+++

関数には引数を渡すことができ、処理の結果を戻り値として返すことができます。引数を使うことで関数に必要なデータを渡し、戻り値を使って関数の結果を取得します。

---

### 引数の使い方

引数は関数定義の際に括弧内に記述します。関数を呼び出すときに、引数に対応する値を渡します。

```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # 出力: 8
```

この例では、`add` 関数は2つの引数 `a` と `b` を受け取り、それらを加算して結果を返します。

---

### デフォルト引数

関数の引数にデフォルト値を設定することができます。これにより、関数呼び出し時に引数を省略した場合でもデフォルト値が使用されます。

```python
def greet(name, message="Hello"):
    return f"{message}, {name}!"

print(greet("Alice"))           # 出力: Hello, Alice!
print(greet("Bob", "Hi"))       # 出力: Hi, Bob!
```

この例では、`greet` 関数は `message` 引数にデフォルト値 "Hello" を持ちます。

---

### キーワード引数

関数を呼び出す際に、引数名を指定して値を渡すことができます。これをキーワード引数と呼びます。

```python
def greet(name, message="Hello"):
    return f"{message}, {name}!"

print(greet(name="Carol", message="Good morning"))  # 出力: Good morning, Carol!
```

この例では、キーワード引数を使って関数を呼び出しています。

---

### 可変長引数

関数が任意の数の引数を受け取れるようにするには、引数の前に `*` を付けます。これにより、複数の引数をタプルとして受け取ることができます。

```python
def sum_all(*numbers):
    return sum(numbers)

print(sum_all(1, 2, 3, 4, 5))  # 出力: 15
```

この例では、`sum_all` 関数は任意の数の引数を受け取り、それらを合計します。

---

### 可変長キーワード引数

関数が任意の数のキーワード引数を受け取れるようにするには、引数の前に `**` を付けます。これにより、複数のキーワード引数を辞書として受け取ることができます。

```python
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

print_info(name="Dave", age=30, country="USA")
# 出力:
# name: Dave
# age: 30
# country: USA
```

この例では、`print_info` 関数は任意のキーワード引数を受け取り、それらを辞書として処理します。

---

### 複数の戻り値

関数は複数の戻り値を返すことができます。複数の値をカンマで区切って返すと、それらはタプルとして返されます。

```python
def calculate(a, b):
    return a + b, a - b, a * b, a / b

result = calculate(10, 5)
print(result)  # 出力: (15, 5, 50, 2.0)

# タプルのアンパック
sum_, diff, prod, quot = calculate(10, 5)
print(sum_)   # 出力: 15
print(diff)   # 出力: 5
print(prod)   # 出力: 50
print(quot)   # 出力: 2.0
```

この例では、`calculate` 関数が4つの値を返し、それらをタプルとして受け取っています。

---

### ラムダ関数

ラムダ関数は、名前を持たない匿名関数です。`lambda` キーワードを使って定義し、短い処理を記述するのに便利です。

```python
# 通常の関数
def add(a, b):
    return a + b

# ラムダ関数
add_lambda = lambda a, b: a + b

print(add(3, 5))        # 出力: 8
print(add_lambda(3, 5)) # 出力: 8
```

この例では、`add` 関数と同じ機能を持つラムダ関数 `add_lambda` を定義しています。

---

## まとめ

この章では、Pythonの関数における引数と戻り値について学びました。関数はコードの再利用性を高め、プログラムの構造を整理するのに役立ちます。次の章では、Pythonの基本的なデータ構造について学びます。データ構造を理解することで、効率的にデータを操作できるようになります。

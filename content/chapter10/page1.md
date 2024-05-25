+++
title = "クラスとオブジェクト"
weight = 11
+++

クラスはオブジェクトの設計図であり、オブジェクトはクラスのインスタンスです。クラスはデータとそれに関連する動作をひとまとめにして管理するための仕組みを提供します。Pythonでは `class` キーワードを使ってクラスを定義します。この章では、クラスとオブジェクトの基本的な使い方について学びます。

---

### クラスの定義

クラスを定義するためには、`class` キーワードを使用します。クラスの属性とメソッドを定義することで、そのクラスのオブジェクトが持つデータと動作を決定します。

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print("ワンワン")
```

この例では、`Dog` クラスを定義し、`name` と `age` という属性、および `bark` というメソッドを持たせています。

---

### オブジェクトの作成

クラスを定義した後、そのクラスのインスタンス（オブジェクト）を作成することができます。オブジェクトを作成するには、クラス名を関数のように呼び出します。

```python
# オブジェクトの作成
my_dog = Dog("Pochi", 3)

# オブジェクトの属性へのアクセス
print(my_dog.name)  # 出力: Pochi
print(my_dog.age)   # 出力: 3

# オブジェクトのメソッドの呼び出し
my_dog.bark()  # 出力: ワンワン
```

この例では、`Dog` クラスのインスタンス `my_dog` を作成し、その属性にアクセスし、メソッドを呼び出しています。

---

### コンストラクタ（__init__ メソッド）

コンストラクタは、オブジェクトが作成されるときに自動的に呼び出される特別なメソッドです。Pythonでは、`__init__` メソッドとして定義します。コンストラクタを使うことで、オブジェクトの初期化処理を行います。

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        print(f"{self.name} が作成されました")

my_dog = Dog("Pochi", 3)
# 出力: Pochi が作成されました
```

この例では、`__init__` メソッドを使ってオブジェクトの初期化処理を行っています。

---

### インスタンスメソッド

インスタンスメソッドは、オブジェクトごとに動作するメソッドです。インスタンスメソッドの第1引数には、通常 `self` を指定します。これにより、メソッド内でそのオブジェクト自身にアクセスできます。

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print(f"{self.name} がワンワンと吠えています")

my_dog = Dog("Pochi", 3)
my_dog.bark()
# 出力: Pochi がワンワンと吠えています
```

この例では、`bark` メソッドが `self` を使ってオブジェクトの `name` 属性にアクセスしています。

---

### クラス属性とインスタンス属性

クラス属性は、クラス全体で共有される属性です。インスタンス属性は、各オブジェクトごとに個別に保持される属性です。

```python
class Dog:
    species = "Canis familiaris"  # クラス属性

    def __init__(self, name, age):
        self.name = name  # インスタンス属性
        self.age = age    # インスタンス属性

# クラス属性へのアクセス
print(Dog.species)  # 出力: Canis familiaris

# インスタンスの作成
my_dog = Dog("Pochi", 3)
print(my_dog.name)  # 出力: Pochi
print(my_dog.age)   # 出力: 3
print(my_dog.species)  # 出力: Canis familiaris
```

この例では、`species` はクラス属性であり、`name` と `age` はインスタンス属性です。

---

### クラスメソッドとスタティックメソッド

クラスメソッドとスタティックメソッドは、インスタンスではなくクラス自体に関連付けられたメソッドです。クラスメソッドは、クラス全体に作用し、スタティックメソッドは独立した処理を行います。

```python
class Dog:
    species = "Canis familiaris"  # クラス属性

    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def get_species(cls):
        return cls.species

    @staticmethod
    def bark_sound():
        return "ワンワン"

# クラスメソッドの呼び出し
print(Dog.get_species())  # 出力: Canis familiaris

# スタティックメソッドの呼び出し
print(Dog.bark_sound())  # 出力: ワンワン
```

この例では、`get_species` はクラスメソッド、`bark_sound` はスタティックメソッドとして定義されています。

---

### 継承

クラスは他のクラスを継承することができます。これにより、既存のクラスの機能を再利用し、拡張することができます。

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f"{self.name} は食事中です")

class Dog(Animal):
    def bark(self):
        print("ワンワン")

my_dog = Dog("Pochi")
my_dog.eat()  # 出力: Pochi は食事中です
my_dog.bark()  # 出力: ワンワン
```

この例では、`Dog` クラスが `Animal` クラスを継承しており、`eat` メソッドを使用できるようになっています。

---

## まとめ

この章では、Pythonのクラスとオブジェクトについて学びました。クラスを使うことで、データとそれに関連する動作をひとまとめにして管理することができ、オブジェクト指向プログラミングの基礎を理解することができます。次の章では、継承とポリモーフィズムについて詳しく学び、クラスの再利用性と柔軟性をさらに高める方法を学びます。

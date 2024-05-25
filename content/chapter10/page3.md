+++
title = "ポリモーフィズム"
weight = 11
+++

ポリモーフィズム（多態性）を使うことで、異なるクラスのオブジェクトが同じメソッドを持つ場合に、同じインターフェースを使ってそれらのメソッドを呼び出すことができます。これにより、コードの柔軟性と再利用性が向上し、より抽象化されたプログラミングが可能になります。

---

### 基本的なポリモーフィズムの例

以下の例では、`Animal` クラスが `speak` メソッドを定義し、`Dog` クラスと `Cat` クラスがそれぞれ `speak` メソッドをオーバーライドしています。`make_animal_speak` 関数は、`Animal` クラスのインスタンスを受け取り、`speak` メソッドを呼び出します。

```python
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print("ワンワン")

class Cat(Animal):
    def speak(self):
        print("ニャー")

def make_animal_speak(animal):
    animal.speak()

dog = Dog()
cat = Cat()
make_animal_speak(dog)  # 出力: ワンワン
make_animal_speak(cat)  # 出力: ニャー
```

この例では、`make_animal_speak` 関数がポリモーフィズムを利用して、`Dog` クラスと `Cat` クラスの `speak` メソッドを同じインターフェースで呼び出しています。

---

### リストを使ったポリモーフィズムの例

ポリモーフィズムは、異なるクラスのオブジェクトをリストなどのデータ構造に格納し、それらを統一的に処理する場合にも便利です。

```python
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print("ワンワン")

class Cat(Animal):
    def speak(self):
        print("ニャー")

animals = [Dog(), Cat(), Dog()]

for animal in animals:
    animal.speak()
# 出力:
# ワンワン
# ニャー
# ワンワン
```

この例では、`animals` リストに `Dog` と `Cat` のインスタンスを格納し、ループ内で `speak` メソッドを呼び出しています。各オブジェクトの具体的な `speak` メソッドが呼び出されることになります。

---

### さらに進んだポリモーフィズムの例

ポリモーフィズムは、インターフェースや抽象基底クラスと組み合わせることで、さらに強力になります。Pythonの `abc` モジュールを使って抽象基底クラスを定義することで、派生クラスが特定のメソッドを実装することを強制できます。

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print("ワンワン")

class Cat(Animal):
    def speak(self):
        print("ニャー")

def make_animal_speak(animal):
    animal.speak()

dog = Dog()
cat = Cat()
make_animal_speak(dog)  # 出力: ワンワン
make_animal_speak(cat)  # 出力: ニャー
```

この例では、`Animal` クラスが抽象基底クラスとなり、`speak` メソッドを抽象メソッドとして定義しています。`Dog` クラスと `Cat` クラスは、この抽象メソッドを具体的に実装しています。

---

### 実際のプロジェクトでのポリモーフィズムの利用例

実際のプロジェクトでは、ポリモーフィズムを使って、異なるデータベースの操作を統一的に扱ったり、異なる形状の図形を同じインターフェースで描画するなど、様々な場面で活用されます。

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def draw(self):
        pass

class Circle(Shape):
    def draw(self):
        print("円を描画します")

class Square(Shape):
    def draw(self):
        print("四角形を描画します")

shapes = [Circle(), Square(), Circle()]

for shape in shapes:
    shape.draw()
# 出力:
# 円を描画します
# 四角形を描画します
# 円を描画します
```

この例では、`Shape` クラスを抽象基底クラスとして定義し、`Circle` クラスと `Square` クラスがそれぞれ `draw` メソッドを実装しています。`shapes` リスト内の各形状オブジェクトの `draw` メソッドを統一的に呼び出すことができます。

---

## まとめ

この章では、Pythonのポリモーフィズムについて学びました。ポリモーフィズムを使うことで、異なるクラスのオブジェクトが同じインターフェースを共有し、統一的に処理することができます。これにより、コードの柔軟性と再利用性が向上します。次の章では、データ分析と可視化について学びます。データを効率的に処理し、視覚的に表現する方法を理解しましょう。

+++
title = "継承"
weight = 11
+++

継承を使うことで、既存のクラスを基に新しいクラスを作成することができます。新しいクラスは既存のクラスの属性とメソッドを引き継ぎ、さらに独自の機能を追加することができます。これにより、コードの再利用性が向上し、オブジェクト指向プログラミングの重要な概念である多態性（ポリモーフィズム）が実現できます。

---

### 基本的な継承

継承を行うには、新しいクラスの定義時に、基底クラス（親クラス）を括弧内に指定します。新しいクラス（子クラス）は、親クラスの属性とメソッドを継承します。

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print("ワンワン")

class Cat(Animal):
    def speak(self):
        print("ニャー")

dog = Dog("Pochi")
cat = Cat("Tama")
dog.speak()  # 出力: ワンワン
cat.speak()  # 出力: ニャー
```

この例では、`Animal` クラスを親クラスとして、`Dog` クラスと `Cat` クラスを作成しています。それぞれの子クラスは、親クラスの `speak` メソッドをオーバーライドしています。

---

### メソッドのオーバーライド

子クラスでは、親クラスで定義されたメソッドを上書き（オーバーライド）することができます。オーバーライドすることで、親クラスのメソッドを再定義し、子クラス固有の振る舞いを実装できます。

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} が音を出しています")

class Dog(Animal):
    def speak(self):
        print(f"{self.name} がワンワンと吠えています")

class Cat(Animal):
    def speak(self):
        print(f"{self.name} がニャーと鳴いています")

dog = Dog("Pochi")
cat = Cat("Tama")
dog.speak()  # 出力: Pochi がワンワンと吠えています
cat.speak()  # 出力: Tama がニャーと鳴いています
```

この例では、`Dog` クラスと `Cat` クラスで `speak` メソッドをオーバーライドしています。

---

### コンストラクタのオーバーライドと親クラスの呼び出し

子クラスでコンストラクタ（`__init__` メソッド）をオーバーライドする場合、親クラスのコンストラクタを呼び出すことができます。これにより、親クラスの初期化処理を引き継ぐことができます。

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)
        self.breed = breed

    def speak(self):
        print(f"{self.name} ({self.breed}) がワンワンと吠えています")

dog = Dog("Pochi", "Shiba Inu")
dog.speak()  # 出力: Pochi (Shiba Inu) がワンワンと吠えています
```

この例では、`Dog` クラスのコンストラクタで `super().__init__(name)` を呼び出すことで、親クラスの `__init__` メソッドを実行しています。

---

### 継承の階層

継承は多段階にわたって行うことができます。あるクラスを継承したクラスをさらに継承することで、継承の階層を作成できます。

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Mammal(Animal):
    def __init__(self, name, has_fur):
        super().__init__(name)
        self.has_fur = has_fur

class Dog(Mammal):
    def __init__(self, name, breed):
        super().__init__(name, True)
        self.breed = breed

    def speak(self):
        print(f"{self.name} ({self.breed}) がワンワンと吠えています")

dog = Dog("Pochi", "Shiba Inu")
dog.speak()  # 出力: Pochi (Shiba Inu) がワンワンと吠えています
print(dog.has_fur)  # 出力: True
```

この例では、`Animal` クラスを `Mammal` クラスが継承し、さらに `Dog` クラスが `Mammal` クラスを継承しています。

---

### 継承とポリモーフィズム

ポリモーフィズムは、異なるクラスのオブジェクトが同じインターフェースを共有し、インターフェースを通じて異なる動作を実装できる特性です。これにより、コードの柔軟性と拡張性が向上します。

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print(f"{self.name} がワンワンと吠えています")

class Cat(Animal):
    def speak(self):
        print(f"{self.name} がニャーと鳴いています")

def make_animal_speak(animal):
    animal.speak()

dog = Dog("Pochi")
cat = Cat("Tama")

make_animal_speak(dog)  # 出力: Pochi がワンワンと吠えています
make_animal_speak(cat)  # 出力: Tama がニャーと鳴いています
```

この例では、`make_animal_speak` 関数が `Animal` クラスのインスタンスを受け取り、ポリモーフィズムを利用して `speak` メソッドを呼び出しています。

---

## まとめ

この章では、Pythonの継承について学びました。継承を使用することで、コードの再利用性を高め、新しいクラスを既存のクラスの機能を基に作成することができます。次の章では、ポリモーフィズムについてさらに詳しく学び、オブジェクト指向プログラミングの強力な特性を理解しましょう。

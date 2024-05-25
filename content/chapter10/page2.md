+++
title = "継承"
weight = 11
+++

継承を使うことで、既存のクラスを基に新しいクラスを作成することができます。新しいクラスは既存のクラスの属性とメソッドを引き継ぎます。

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
dog.speak()  # ワンワン
cat.speak()  # ニャー
```

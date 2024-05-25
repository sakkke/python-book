+++
title = "ポリモーフィズム"
weight = 11
+++

ポリモーフィズムを使うことで、異なるクラスのオブジェクトが同じメソッドを持つ場合に、同じインターフェースを使ってそれらのメソッドを呼び出すことができます。

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
make_animal_speak(dog)  # ワンワン
make_animal_speak(cat)  # ニャー
```

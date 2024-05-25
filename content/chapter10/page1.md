+++
title = "クラスとオブジェクト"
weight = 11
+++

クラスはオブジェクトの設計図であり、オブジェクトはクラスのインスタンスです。Pythonでは `class` キーワードを使ってクラスを定義します。

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print("ワンワン")

# オブジェクトの作成
my_dog = Dog("Pochi", 3)
print(my_dog.name)  # Pochi
my_dog.bark()  # ワンワン
```

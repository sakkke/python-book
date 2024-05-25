+++
title = "ファイルの読み書き"
weight = 9
+++

Pythonでは、ファイルの読み書きを簡単に行うことができます。

```python
# ファイルの書き込み
with open("example.txt", "w") as file:
    file.write("Hello, World!")

# ファイルの読み込み
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

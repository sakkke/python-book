+++
title = "独自例外の作成"
weight = 10
+++

独自の例外クラスを作成することで、特定のエラー条件に対してカスタマイズされた処理を行うことができます。独自の例外クラスは、標準の `Exception` クラスを継承して作成します。

```python
class CustomError(Exception):
    pass

try:
    raise CustomError("これは独自のエラーです")
except CustomError as e:
    print(e)
```

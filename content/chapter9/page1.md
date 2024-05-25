+++
title = "例外処理（try、except）"
weight = 10
+++

プログラム実行中にエラーが発生した場合、それを適切に処理するために例外処理を使用します。Pythonでは `try`、`except` ブロックを使って例外処理を行います。

```python
try:
    # 例外が発生する可能性があるコード
    result = 10 / 0
except ZeroDivisionError:
    # 例外が発生した場合の処理
    print("ゼロによる除算エラーが発生しました")
```

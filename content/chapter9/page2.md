+++
title = "独自例外の作成"
weight = 10
+++

独自の例外クラスを作成することで、特定のエラー条件に対してカスタマイズされた処理を行うことができます。独自の例外クラスは、標準の `Exception` クラスを継承して作成します。これにより、特定の状況に応じた例外を発生させることができ、エラーハンドリングがより柔軟になります。

---

### 独自例外クラスの基本的な作成方法

独自の例外クラスを作成するには、`Exception` クラスを継承し、新しいクラスを定義します。必要に応じて、エラーメッセージを受け取るコンストラクタを追加できます。

```python
class CustomError(Exception):
    """独自の例外クラス"""
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

try:
    raise CustomError("これは独自のエラーです")
except CustomError as e:
    print(f"エラーが発生しました: {e}")
```

この例では、`CustomError` クラスを定義し、その例外を発生させた後、キャッチしてエラーメッセージを表示しています。

---

### 複数の独自例外クラスの作成

複数の独自例外クラスを作成することで、エラーの種類ごとに異なる処理を行うことができます。これにより、特定のエラー条件に対してより細かい制御が可能になります。

```python
class ValidationError(Exception):
    """入力の検証エラーを表す例外クラス"""
    pass

class DatabaseError(Exception):
    """データベース関連のエラーを表す例外クラス"""
    pass

def validate_data(data):
    if not isinstance(data, dict):
        raise ValidationError("データは辞書型でなければなりません")

def connect_to_database():
    raise DatabaseError("データベースに接続できません")

try:
    validate_data("これは辞書ではありません")
except ValidationError as e:
    print(f"検証エラーが発生しました: {e}")
except DatabaseError as e:
    print(f"データベースエラーが発生しました: {e}")
```

この例では、`ValidationError` と `DatabaseError` の2つの独自例外クラスを定義し、それぞれのエラーを発生させて適切に処理しています。

---

### 独自例外クラスにカスタム属性を追加する

独自例外クラスにカスタム属性を追加することで、例外に関する追加情報を提供することができます。例えば、エラーコードや詳細なエラーメッセージを含めることができます。

```python
class CustomError(Exception):
    """カスタムエラークラス"""
    def __init__(self, message, code):
        self.message = message
        self.code = code
        super().__init__(self.message)

try:
    raise CustomError("これは独自のエラーです", 500)
except CustomError as e:
    print(f"エラーが発生しました: {e.message} (コード: {e.code})")
```

この例では、`CustomError` クラスに `message` と `code` のカスタム属性を追加しています。例外が発生した場合、それらの属性を使って詳細なエラーメッセージを表示します。

---

### ネストされた例外と例外の再発生

独自例外クラスを使う際、例外を再発生（再スロー）させて外部で処理させることもできます。これにより、例外が発生した場所と、それが処理された場所の両方で情報を提供できます。

```python
class CustomError(Exception):
    """独自の例外クラス"""
    pass

def process_data(data):
    try:
        if not isinstance(data, dict):
            raise CustomError("データは辞書型でなければなりません")
    except CustomError as e:
        print(f"内部でエラーが発生しました: {e}")
        raise  # 例外を再発生させる

try:
    process_data("これは辞書ではありません")
except CustomError as e:
    print(f"外部でエラーがキャッチされました: {e}")
```

この例では、`process_data` 関数内で発生した `CustomError` を再発生させ、外部の `try` ブロックでキャッチして処理しています。

---

## まとめ

この章では、独自例外の作成方法について学びました。独自の例外クラスを作成することで、特定のエラー条件に対してカスタマイズされた処理を行うことができ、エラーハンドリングがより柔軟になります。次の章では、オブジェクト指向プログラミング（OOP）について学びます。クラスとオブジェクトを使って、より複雑なデータ構造とロジックを効果的に管理する方法を理解しましょう。

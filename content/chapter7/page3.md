+++
title = "外部パッケージのインストールと使用（pip）"
weight = 8
+++

Pythonでは、多くの外部パッケージを簡単にインストールして使用できます。`pip`はPythonのパッケージ管理システムで、これを使ってパッケージをインストールします。

```bash
# pandasのインストール
pip install pandas
```

```python
# pandasのインポート
import pandas as pd
# DataFrameの作成
df = pd.DataFrame({"Name": ["Alice", "Bob"], "Age": [25, 30]})
print(df)
```

+++
title = "pandasの基本"
weight = 12
+++

pandasは、データ操作や分析を簡単に行うためのライブラリです。DataFrameを使ってデータを操作します。

```python
import pandas as pd

# DataFrameの作成
data = {"Name": ["Alice", "Bob"], "Age": [25, 30]}
df = pd.DataFrame(data)
print(df)

# データのフィルタリング
filtered_df = df[df["Age"] > 25]
print(filtered_df)
```

+++
title = "CSVファイルの操作"
weight = 9
+++

CSVファイルは、データを表形式で保存するための一般的なフォーマットです。`csv`モジュールを使って操作します。

```python
import csv

# CSVファイルの書き込み
with open("example.csv", "w", newline='') as file:
    writer = csv.writer(file)
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 25])
    writer.writerow(["Bob", 30])

# CSVファイルの読み込み
with open("example.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

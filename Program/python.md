# Python 記法まとめ

## リンク集

### ドキュメント
#### 公式
[公式ドキュメント](https://docs.python.org/ja/3/)

#### ライブラリ系
[MySQL Connector/Python](https://dev.mysql.com/doc/connector-python/en/)
[pandas](https://pandas.pydata.org/docs/)
[discord.py](https://discordpy.readthedocs.io/ja/latest/index.html)
[openpyxl](https://openpyxl.readthedocs.io/en/stable/)
[matplotlib](https://matplotlib.org/)

#### その他参考サイト
[matplotlib入門](https://aiacademy.jp/media/?p=154)


## 標準機能

### Hello,World

```python {cmd}
print("hello,world!")
```

### 標準入力(コードチャンクでは動作しない)

```python
a = input()
b = input("好きな文字を入力してください")
```

## ライブラリ

### mysql

### pandas

### discord

### postgresql

### json

書き込み
```python {cmd}
import datetime as dt
import json
dict = {"key1":12345678,
        "key2":"abc"}
todate = dt.date.today()
path = f"./{todate.strftime('%Y%m%d')}test.json"
with open(path, mode='w') as f:
  json.dump(dict, f)
```

### datetime
```python {cmd}
import datetime as dt
now = dt.datetime.now()
todate = dt.date.today()
print(now)
print(todate.strftime("%Y/%m/%d"))
```

### pathlib
```python {cmd}
# -*- coding: utf-8 -*-
import pprint
from pathlib import Path
p_dir = Path(".")
print(p_dir)
print(p_dir.is_file())
print(p_dir.is_dir())
print(p_dir.exists())
# print(list(p_dir.iterdir()))

joinedPath = p_dir / "newDir"
joinedPath.mkdir(exist_ok = False)
joinedPath = joinedPath / "test.txt"
joinedPath.touch()
# pprint.pprint(list(p_dir.iterdir()))
newFile = Path("./new.txt")
newFile.touch()



```



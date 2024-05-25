+++
title = "Pythonのインストール方法"
weight = 3
+++

Pythonを使うためには、まずPython自体をインストールする必要があります。Pythonの公式サイトから最新バージョンをダウンロードし、インストールを行います。

- **Windows**
  - Python公式サイト（[python.org](https://www.python.org/)）からインストーラーをダウンロードします。
  - インストーラーを実行し、「Add Python to PATH」にチェックを入れてインストールを進めます。

- **macOS**
  - macOSにはPython 2.xがプリインストールされていますが、Python 3.xをインストールすることをお勧めします。
  - Homebrewを使用してインストールするのが簡単です。ターミナルを開き、以下のコマンドを実行します：
    ```bash
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    brew install python
    ```

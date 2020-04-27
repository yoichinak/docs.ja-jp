---
title: 追加の ML.NET 依存関係のインストール
description: ML.NET パッケージが依存しているものの NuGet パッケージと共にインストールされない、ネイティブ ライブラリをインストールする方法について説明します
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c427439d0950bfea38f1d6d11af84216e0f1965f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021848"
---
# <a name="install-extra-mlnet-dependencies"></a>追加の ML.NET 依存関係のインストール

ほとんどの場合、すべてのオペレーティング システムで、ML.NET をインストールすることは、適切な NuGet パッケージを参照するのと同じくらい簡単です。

```bash
dotnet add package Microsoft.ML
```

ただし、場合によっては、特にネイティブ コンポーネントが必要であれば、追加のインストール要件が生じます。 このドキュメントでは、これらのケースでのインストール要件について説明します。 各セクションは、追加の依存関係を持つ特定の `Microsoft.ML.*` NuGet パッケージによって分類されます。

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft.ML.TimeSeries、Microsoft.ML.AutoML

これらのパッケージはどちらも `Microsoft.ML.MKL.Redist` に依存しており、これは `libiomp` に依存しています。

### <a name="windows"></a>Windows

追加のインストール手順は必要ありません。 プロジェクトに NuGet パッケージを追加すると、ライブラリがインストールされます。

### <a name="linux"></a>Linux

1. リポジトリの GPG キーをインストールします。

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. MKL の APT リポジトリを追加します。

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. パッケージの更新

    ```bash
    sudo apt-get update
    ```

4. MKL をインストールします。

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    次に例を示します。

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    `libiomp.so` の場所を決定します。

    ```bash
    find /opt -name "libiomp5.so"
    ```

    次に例を示します。

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. この場所を読み込みライブラリ パスに追加します。

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. `Homebrew` と共にライブラリをインストールします。

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```

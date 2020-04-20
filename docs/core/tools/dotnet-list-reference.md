---
title: dotnet list reference コマンド
description: dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463644"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン

## <a name="name"></a>name

`dotnet list reference` - プロジェクト間参照を列挙します。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

## <a name="description"></a>[説明]

`dotnet list reference` コマンドは、特定のプロジェクトまたはソリューションのプロジェクト参照を列挙する便利なオプションを提供します。

## <a name="arguments"></a>引数

* **`PROJECT | SOLUTION`**

  参照の一覧取得に使うプロジェクトまたはソリューション ファイルを指定します。 指定されていない場合、コマンドではプロジェクト ファイルを現在のディレクトリで検索します。

## <a name="options"></a>オプション

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

## <a name="examples"></a>例

* 指定したプロジェクトのプロジェクト参照を列挙する:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* 現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:

  ```dotnetcli
  dotnet list reference
  ```

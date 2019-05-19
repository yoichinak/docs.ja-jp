---
title: dotnet list reference コマンド
description: dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。
ms.date: 12/03/2018
ms.openlocfilehash: c0b88c4a0af4469d7ddc9e0a9368bb1b2d9d20b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632407"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet list reference` - プロジェクト間参照を列挙します。

## <a name="synopsis"></a>構文

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>説明

`dotnet list reference` コマンドは、特定のプロジェクトまたはソリューションのプロジェクト参照を列挙する便利なオプションを提供します。

## <a name="arguments"></a>引数

* **`PROJECT`**

  参照の一覧取得に使うプロジェクト ファイルを指定します。 指定されていない場合、コマンドではプロジェクト ファイルを現在のディレクトリで検索します。

## <a name="options"></a>オプション

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

## <a name="examples"></a>使用例

* 指定したプロジェクトのプロジェクト参照を列挙する:

  ```console
  dotnet list app/app.csproj reference
  ```

* 現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:

  ```console
  dotnet list reference
  ```

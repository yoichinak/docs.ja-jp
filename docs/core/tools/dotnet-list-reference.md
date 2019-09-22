---
title: dotnet list reference コマンド
description: dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117682"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**このトピックの対象: ✓** .NET Core 1.x SDK 以降のバージョン

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>name

`dotnet list reference` - プロジェクト間参照を列挙します。

## <a name="synopsis"></a>構文

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>説明

`dotnet list reference` コマンドは、特定のプロジェクトまたはソリューションのプロジェクト参照を列挙する便利なオプションを提供します。

## <a name="arguments"></a>引数

* **`PROJECT | SOLUTION`**

  参照の一覧取得に使うプロジェクトまたはソリューション ファイルを指定します。 指定されていない場合、コマンドではプロジェクト ファイルを現在のディレクトリで検索します。

## <a name="options"></a>オプション

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

## <a name="examples"></a>使用例

* 指定したプロジェクトのプロジェクト参照を列挙する:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* 現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:

  ```dotnetcli
  dotnet list reference
  ```

---
title: dotnet nuget delete コマンド
description: dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: e1362413aa6458674518d68340634741994b34a3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632059"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet nuget delete` - サーバーからパッケージを削除または一覧から削除します。

## <a name="synopsis"></a>構文

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a>説明

`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。 [nuget.org](https://www.nuget.org/) の場合、この操作ではパッケージを一覧から削除します。

## <a name="arguments"></a>引数

* **`PACKAGE_NAME`**

  削除するパッケージの名前または ID です。

* **`PACKAGE_VERSION`**

  削除するパッケージのバージョンです。

## <a name="options"></a>オプション

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`--force-english-output`**

  インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`--interactive`**

  コマンドが認証などの操作をブロックして、手動アクションを要求することを許可します。 .NET Core 2.2 SDK 以降、使用できるオプションです。

* **`-k|--api-key <API_KEY>`**

  サーバーの API キーです。

* **`--no-service-endpoint`**

  ソース URL に "api/v2/package" を追加しません。 .NET Core 2.1 SDK 以降、使用できるオプションです。

* **`--non-interactive`**

  ユーザーに入力や確認のメッセージ画面を表示しません。

* **`-s|--source <SOURCE>`**

  サーバー URL を指定します。 nuget.org でサポートされている URL には、`https://www.nuget.org`、`https://www.nuget.org/api/v3`、および `https://www.nuget.org/api/v2/package` が含まれます。 プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`--force-english-output`**

  インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`-k|--api-key <API_KEY>`**

  サーバーの API キーです。

* **`--non-interactive`**

  ユーザーに入力や確認のメッセージ画面を表示しません。

* **`-s|--source <SOURCE>`**

  サーバー URL を指定します。 nuget.org でサポートされている URL には、`https://www.nuget.org`、`https://www.nuget.org/api/v3`、および `https://www.nuget.org/api/v2/package` が含まれます。 プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。

---

## <a name="examples"></a>使用例

* `Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* ユーザーに資格情報やその他の入力を求めずに、`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```

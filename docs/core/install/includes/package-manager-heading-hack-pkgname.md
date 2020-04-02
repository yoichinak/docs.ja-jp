---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134105"
---

パッケージ マネージャーのフィードに追加されたパッケージは、`{product}-{type}-{version}` のハック可能な形式で名前が付けられます。

- **product**\
インストールする .NET 製品の種類。 有効なオプションは次のとおりです。

  - dotnet
  - aspnetcore

- **type**\
SDK またはランタイムを選択します。 有効なオプションは次のとおりです。

  - SDK
  - ランタイム

- **version**\
インストールする SDK またはランタイムのバージョン。 この記事では常に、サポートされている最新バージョンの手順について説明します。 有効なオプションは、次のようなリリース バージョンです。

  - 3.1
  - 3.0
  - 2.1

  ダウンロードしようとしている SDK/ランタイムが Linux ディストリビューションで使用できない可能性があります。 サポートされているディストリビューションの一覧については、「[.NET Core の依存関係と要件](../dependencies.md?pivots=os-linux)」を参照してください。

### <a name="examples"></a>使用例

- ASP.NET Core 3.1 ランタイムをインストールする: `aspnetcore-runtime-3.1`
- .NET Core 2.1 ランタイムをインストールする: `dotnet-runtime-2.1`
- .NET Core 3.1 SDK をインストールする: `dotnet-sdk-3.1`

### <a name="package-missing"></a>パッケージがない

パッケージ バージョンの組み合わせが正しくない場合は、使用できません。 たとえば、ASP.NET Core SDK がない場合、SDK コンポーネントは .NET Core SDK に含まれています。 値 `aspnetcore-sdk-2.2` は正しくありません。`dotnet-sdk-2.2` にする必要があります .NET Core によってサポートされている Linux ディストリビューションの一覧については、「[.NET Core の依存関係と要件](../dependencies.md?pivots=os-linux)」を参照してください。

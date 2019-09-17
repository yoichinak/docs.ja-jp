---
title: Visual Studio で LINQ to DataSet プロジェクトを作成する
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 8b905c65575c3c567459d843b2a5d1606bc63228
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783779"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>方法: Visual Studio で LINQ to DataSet プロジェクトを作成する

LINQ プロジェクトの種類によっては、特定のアセンブリ参照とインポートされた名前空間C#(Visual Basic) または [using](../../../csharp/language-reference/keywords/using-directive.md) ディレクティブ () が必要になります。 LINQ の最小要件*は、の system.object への*参照と`using`の<xref:System.Linq>ディレクティブです。

これらの要件は、Visual Studio 2017 で新しいC#コンソールアプリプロジェクトを作成した場合に既定で提供されます。 以前のバージョンの Visual Studio からプロジェクトをアップグレードする場合は、これらの LINQ 関連の参照を手動で指定することが必要になる場合があります。

LINQ to DataSet*には、次の 2*つの追加の参照が必要*です。*

> [!NOTE]
> コマンドプロンプトからビルドする場合は、 *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*で LINQ 関連の dll を手動で参照する必要があります。

## <a name="to-enable-linq-to-dataset-functionality"></a>LINQ to DataSet 機能を有効にするには

既存のプロジェクトで LINQ to DataSet 機能を有効にするには、次の手順に従います。

1. **System. Core**、system.string、および**datasetextensions** **への参照**を追加します。

   **ソリューションエクスプローラー**で、 **[参照]** ノードを右クリックし、 **[参照の追加]** を選択します。 **[参照マネージャー]** ダイアログボックスで、 **[Core**]、 **[システムデータ]** 、および **[データ拡張子]** を選択します。 **[OK]** を選択します。

1. [Using](../../../csharp/language-reference/keywords/using-directive.md)ディレクティブ (または Visual Basic 内の[Imports ステートメント](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md))**を system.string および system.string**に**追加します。**

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. 必要に応じて`using` 、データベースへ`Imports`の接続方法に応じ**て、** **システム**のディレクティブ (またはステートメント) を追加します。

## <a name="see-also"></a>関連項目

- [LINQ to DataSet を使ってみる](getting-started-linq-to-dataset.md)

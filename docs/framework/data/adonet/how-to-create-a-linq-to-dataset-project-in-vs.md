---
title: LINQ to DataSet プロジェクトで Visual Studio を作成します。
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667049"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>方法: LINQ to DataSet プロジェクトで Visual Studio を作成します。

LINQ プロジェクトの種類は、特定のアセンブリ参照とインポートされた名前空間 (Visual Basic) が必要です。 または[を使用して](../../../csharp/language-reference/keywords/using-directive.md)ディレクティブ (c#)。 LINQ の最低要件への参照を*System.Core.dll*と`using`ディレクティブを<xref:System.Linq>します。

これらの要件は、Visual Studio 2017 で新しい c# コンソール アプリ プロジェクトを作成する場合に、既定で提供されます。 プロジェクトを Visual Studio の以前のバージョンからアップグレードする場合は、これらの LINQ に関連する参照を手動で指定する必要があります。

LINQ to DataSet を 2 つの他の参照を必要と*System.Data.dll*と*System.Data.DataSetExtensions.dll*します。

> [!NOTE]
> コマンド プロンプトから構築する場合は、LINQ 関連の Dll を手動で参照する必要があります *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*します。

## <a name="to-enable-linq-to-dataset-functionality"></a>LINQ to DataSet 機能を有効にするには

LINQ を既存のプロジェクトで DataSet 機能を有効にする次の手順に従います。

1. 参照を追加**System.Core**、 **System.Data**、および**System.Data.DataSetExtensions**します。

   **ソリューション エクスプ ローラー**を右クリックし、**参照**ノード**参照の追加**します。 **参照マネージャー**ダイアログ ボックスで、 **System.Core**、 **System.Data**、および**System.Data.DataSetExtensions**します。 **[OK]** を選択します。

1. 追加[を使用して](../../../csharp/language-reference/keywords/using-directive.md)ディレクティブ (または[Imports ステートメント](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)Visual basic) の**System.Data**と**System.Linq**します。

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. 必要に応じて、追加、`using`ディレクティブ (または`Imports`ステートメント) の**System.Data.Common**または**System.Data.SqlClient**データベースに接続する方法によって異なります。

## <a name="see-also"></a>関連項目

- [LINQ to DataSet を概要します。](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)

---
title: '方法: 接続文字列を定義する'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 7fb722acbb13b3502d004978581701cc70118ff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606105"
---
# <a name="how-to-define-the-connection-string"></a>方法: 接続文字列を定義する

このトピックでは、概念モデルに接続するための接続文字列を定義する方法について説明します。 このトピックではに基づいて、 [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念モデル。 AdventureWorks Sales Model は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ドキュメントのタスク関連のトピック全般で使用されます。 このトピックでは、既に構成されていることを想定しています、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] AdventureWorks Sales Model が定義されているとします。 詳細については、「[方法 :モデルを定義して、マッピング ファイルを手動で](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))します。 このトピックの手順でに含まれるも[方法。Entity Framework プロジェクトを手動で構成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))します。

> [!NOTE]
> 使用する場合、[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)]ウィザード、Visual Studio プロジェクトに自動的に .edmx ファイルを生成し、使用するプロジェクトを構成、、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]します。 詳細については、「[方法 :エンティティ データ モデル ウィザードを使用します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

## <a name="to-define-the-entity-framework-connection-string"></a>Entity Framework 接続文字列を定義するには

- プロジェクトのアプリケーション構成ファイル (app.config) を開き、次の接続文字列を追加します。

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

プロジェクトがアプリケーション構成ファイルを持たない場合は、1 つを選択して、追加**新しい項目の追加**から、**プロジェクト** メニューを選択すると、**全般**カテゴリで、選択**アプリケーション構成ファイル**、 をクリックし、**追加**します。

## <a name="see-also"></a>関連項目

- [クイック スタート](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [方法: 新しい .edmx ファイルを作成します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

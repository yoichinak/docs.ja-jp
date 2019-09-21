---
title: '方法: 接続文字列を定義する'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854662"
---
# <a name="how-to-define-the-connection-string"></a>方法: 接続文字列を定義する

このトピックでは、概念モデルに接続するための接続文字列を定義する方法について説明します。 このトピックは、 [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念モデルに基づいています。 AdventureWorks Sales Model は、Entity Framework ドキュメントのタスク関連のトピック全体で使用されます。 このトピックでは、Entity Framework が既に構成されており、AdventureWorks Sales Model が定義されていることを前提としています。 詳細については、「[方法 :モデルファイルとマッピングファイル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))を手動で定義します。 このトピックの手順は、次の方法[でも説明されています。Entity Framework プロジェクト](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))を手動で構成します。

> [!NOTE]
> Visual Studio プロジェクトで Entity Data Model ウィザードを使用すると、.edmx ファイルが自動的に生成され、Entity Framework を使用するようにプロジェクトが構成されます。 詳細については、「[方法 :Entity Data Model ウィザードの使用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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

プロジェクトにアプリケーション構成ファイルがない場合は、**プロジェクト** メニューの **新しい項目の追加** をクリックして**全般** カテゴリを選択し、**アプリケーション構成ファイル** を選択してから、次へ をクリックして追加することができます。を**追加**します。

## <a name="see-also"></a>関連項目

- [クイック スタート](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [方法: 新しい .edmx ファイルを作成します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

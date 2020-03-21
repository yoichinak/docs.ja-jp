---
title: 接続文字列を定義する方法
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150572"
---
# <a name="how-to-define-the-connection-string"></a>接続文字列を定義する方法

このトピックでは、概念モデルに接続するための接続文字列を定義する方法について説明します。 このトピックは[、AdventureWorks の販売](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念モデルに基づいています。 AdventureWorks の販売モデルは、エンティティ フレームワークのドキュメントのタスク関連のトピック全体で使用されます。 このトピックでは、エンティティ フレームワークを既に設定し、AdventureWorks 販売モデルを定義していることを前提としています。 詳細については、「[方法 : モデル ファイルとマッピング ファイルを手動で定義する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))」を参照してください。 このトピックの手順は、「[方法: エンティティ フレームワーク プロジェクトを手動で構成する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))」にも含まれています。

> [!NOTE]
> Visual Studio プロジェクトでエンティティ データ モデル ウィザードを使用すると、.edmx ファイルが自動的に生成され、エンティティ フレームワークを使用するようにプロジェクトが構成されます。 詳細については、「[方法 : エンティティ データ モデル ウィザードを使用する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。

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

プロジェクトにアプリケーション構成ファイルがない場合は、[**プロジェクト**] メニューの **[新しい項目の追加**] をクリックし、[**全般**] カテゴリを選択して [**アプリケーション構成ファイル**] を選択し、[追加] をクリックして**追加**できます。

## <a name="see-also"></a>関連項目

- [クイック スタート](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [方法: 新しい .edmx ファイルを作成する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

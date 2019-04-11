---
title: ASP.NET アプリケーションでの SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 67c1307bb18b3e86e05b56f4853a39f6831ab9cc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313594"
---
# <a name="sqldependency-in-an-aspnet-application"></a>ASP.NET アプリケーションでの SqlDependency
ここでは、ASP.NET の <xref:System.Data.SqlClient.SqlDependency> オブジェクトを使用して、<xref:System.Web.Caching.SqlCacheDependency> を間接的に使用する方法の例を示します。 <xref:System.Web.Caching.SqlCacheDependency> オブジェクトでは <xref:System.Data.SqlClient.SqlDependency> を使用して通知をリッスンし、キャッシュを適切に更新します。  
  
> [!NOTE]
>  サンプル コードは、内のスクリプトを実行することによって、クエリ通知を有効にした前提としています。[クエリ通知を有効にする](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)します。  
  
## <a name="about-the-sample-application"></a>サンプル アプリケーションについて  
 サンプル アプリケーションでは、単一の ASP.NET Web ページを使用して、製品情報を表示、 **AdventureWorks**で SQL Server データベース、<xref:System.Web.UI.WebControls.GridView>コントロール。 ページが読み込まれる際に、<xref:System.Web.UI.WebControls.Label> コントロールに現在の時刻が入力されます。 次に、<xref:System.Web.Caching.SqlCacheDependency> オブジェクトを定義し、最長 3 分間キャッシュ データを格納するように <xref:System.Web.Caching.Cache> オブジェクトのプロパティを設定します。 その後、データベースに接続し、データを取得します。 ページが読み込まれ、アプリケーションが実行されると、ASP.NET ではキャッシュからデータが取得されます。これは、ページ上の時刻が変更されないことで確認できます。 監視しているデータが変化すると、ASP.NET によりキャッシュが無効化され、`GridView` コントロールに最新データが再入力されることで、`Label` コントロールに表示される時刻が更新されます。  
  
## <a name="creating-the-sample-application"></a>サンプル アプリケーションの作成  
 サンプル アプリケーションを作成して実行するには、次の手順に従います。  
  
1. 新しい ASP.NET Web サイトを作成します。  
  
2. Default.aspx ページに <xref:System.Web.UI.WebControls.Label> コントロールと <xref:System.Web.UI.WebControls.GridView> コントロールを追加します。  
  
3. ページのクラス モジュールを開き、次のディレクティブを追加します。  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. ページの `Page_Load` イベントに次のコードを追加します。  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. `GetConnectionString` および `GetSQL` という 2 つのヘルパー メソッドを追加します。 定義される接続文字列は、統合セキュリティを利用します。 使用しているアカウントが必要なデータベース権限とのことを確認する必要があります、サンプル データベース**AdventureWorks**が通知を有効にします。
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>アプリケーションのテスト  
 このアプリケーションは Web フォームに表示されるデータをキャッシングし、操作が行われなければ 3 分ごとにデータを更新します。 データベースに変化があれば、キャッシュは直ちに更新されます。 Visual Studio からアプリケーションを実行すると、ブラウザーにページが読み込まれます。 表示されるキャッシュ更新時刻は、最後にキャッシュが更新された時刻を示します。 3 分間の待機後、ページを更新し、ポストバック イベントが発生します。 ページに表示される時刻が変更されることに注意してください。 3 分経過する前にページを更新した場合は、ページに表示される時刻は変わりません。  
  
 次に、Transact-SQL の UPDATE コマンドを使用して、データベースのデータを更新し、ページを更新します。 表示される時刻を見ると、データベースの新しいデータを使ってキャッシュが更新されたことがわかります。 キャッシュは更新されますが、ページに表示される時刻はポストバック イベントが発生するまで変更されないことに注意してください。  
  
## <a name="see-also"></a>関連項目

- [SQL Server のクエリ通知](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

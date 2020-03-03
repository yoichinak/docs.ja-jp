---
title: SQL Server のデータベース ミラーリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: b18c67f5573d375fe0872d76d69a1f0aafa7e7f6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040439"
---
# <a name="database-mirroring-in-sql-server"></a>SQL Server のデータベース ミラーリング
SQL Server のデータベース ミラーリング機能を使用すると、スタンバイ サーバー上に SQL Server データベースのコピー (ミラー) を保持できます。 ミラーリングは、常にデータのコピーが 2 つ別々に存在することを保証し、高可用性とデータの完全な冗長性をもたらします。 .NET Data Provider for SQL Server では、データベース ミラーリングが暗黙的にサポートされているため、SQL Server データベース用に構成されている場合は、開発者が操作を行ったり、コードを作成したりする必要はありません。 さらに、<xref:System.Data.SqlClient.SqlConnection> オブジェクトは、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 内のフェールオーバー パートナー サーバーの名前を指定できる明示的な接続モードをサポートします。  
  
 次の簡略化された一連のイベントは、ミラーリング用に構成されているデータベースを対象にする <xref:System.Data.SqlClient.SqlConnection> オブジェクトで発生します。  
  
1. クライアント アプリケーションが正常にプリンシパル データベースに接続し、クライアント上でキャッシュされたパートナー サーバーの名前をサーバーが返信します。  
  
2. プリンシパル データベースが存在するサーバーで障害が発生したか、接続が中断された場合、接続とトランザクションの状態は失われます。 クライアント アプリケーションは、プリンシパル データベースへの接続を再確立しようとして、失敗します。  
  
3. 次に、クライアント アプリケーションでは、パートナー サーバー上のミラー データベースへの接続を透過的に確立しようとします。 この処理に成功すると、新しいプリンシパル データベースとなるミラー データベースに、接続がリダイレクトされます。  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>接続文字列でのフェールオーバー パートナーの指定  
 接続文字列でフェールオーバー パートナー サーバーの名前を指定すると、クライアント アプリケーションが最初に接続するときにプリンシパル データベースを使用できない場合、クライアントはフェールオーバー パートナーへの接続を透過的に試行します。  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 接続文字列のフェールオーバー パートナー サーバーの名前を省略すると、クライアント アプリケーションが最初に接続するときにプリンシパル データベースが使用できない場合、<xref:System.Data.SqlClient.SqlException> が発生します。  
  
 <xref:System.Data.SqlClient.SqlConnection> が正常に開かれた場合、サーバーからフェールオーバー パートナーの名前が返され、接続文字列に指定されている値を置き換えます。  
  
> [!NOTE]
> データベース ミラーリング シナリオでは、接続文字列で初期カタログやデータベース名を明示的に指定する必要があります。 クライアントが、初期カタログやデータベースが明示的に指定されていない接続に関するフェールオーバー情報を受信する場合は、このフェールオーバー情報はキャッシュされず、アプリケーションはプリンシパル サーバーでの障害発生時にフェールオーバーを試行しません。 接続文字列にフェールオーバー パートナーの値が含まれていても、初期カタログまたはデータベースの値が含まれていない場合、`InvalidArgumentException` が発生します。  
  
## <a name="retrieving-the-current-server-name"></a>現在のサーバー名の取得  
 フェールオーバーの場合には、<xref:System.Data.SqlClient.SqlConnection.DataSource%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを使って、現在の接続が実際に接続されているサーバーの名前を取得できます。 次のコード フラグメントでは、アクティブなサーバーの名前を取得します。この場合、接続変数は開いている <xref:System.Data.SqlClient.SqlConnection> を参照することを前提としています。  
  
 フェールオーバーイベントが発生し、接続がミラーサーバーに切り替わると、**データソース**プロパティが更新され、ミラー名が反映されます。  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient ミラーリングの動作  
 クライアントは、常に現在のプリンシパル サーバーに接続しようとします。 接続に失敗した場合は、フェールオーバー パートナーに接続しようとします。 ミラー データベースが既にパートナー サーバー上でプリンシパル ロールに切り替わっている場合、接続は正常に行われ、新しいプリンシパルとミラー間のマッピングがクライアントに送信されて <xref:System.AppDomain> の呼び出しの有効期間の間キャッシュされます。 永続ストレージに格納されることはなく、別の**AppDomain**またはプロセスでの後続の接続では使用できません。 ただし、同じ**AppDomain**内の後続の接続でも使用できます。 同じコンピューターまたは別のコンピューター上で実行されている別の**AppDomain**またはプロセスには、常に接続のプールがあり、これらの接続はリセットされないことに注意してください。 この場合、プライマリデータベースがダウンした場合、各プロセスまたは**AppDomain**は1回失敗し、プールは自動的にクリアされます。  
  
> [!NOTE]
> サーバーのミラーリング サポートは、データベースごとに構成されます。 複数部分から成る名前を使用するか、現在のデータベースを変更することにより、プリンシパル/ミラー セットに含まれない他のデータベースに対してデータの操作が実行された場合、これらの他のデータベースへの変更は障害の発生時には反映されません。 ミラー化されていないデータベース内でデータが変更された場合、エラーは発生しません。 開発者は、このような操作の考えられる影響を評価する必要があります。  
  
## <a name="database-mirroring-resources"></a>データベース ミラーリングに関するリソース  
 ミラーリングの構成、展開、および管理の概念に関するドキュメントと情報については、SQL Server のドキュメントで次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[データベースミラーリング](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|SQL Server でのミラーリングの設定と構成方法について説明します。|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)

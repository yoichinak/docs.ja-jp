---
title: ADO.NET での side-by-side 実行
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: d20d8e81d76284509d6fe733e4f283a9ab39cb00
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877091"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET での side-by-side 実行
.NET Framework でのサイド バイ サイドで実行、アプリケーションのコンパイル対象のバージョンを排他的に使用して、インストールされている .NET Framework の複数のバージョンをあるコンピューター上でアプリケーションを実行する機能があります。 サイド バイ サイドで実行を構成する方法の詳細については、次を参照してください。[サイド バイ サイド実行](../../../../docs/framework/deployment/side-by-side-execution.md)します。  
  
 .NET Framework の 1 つのバージョンを使用してコンパイルされたアプリケーションは、.NET Framework の別のバージョンで実行できます。 ただし、バージョンの .NET Framework のインストールされている各バージョンのアプリケーションをコンパイルして、別々 に実行することお勧めします。 どちらのシナリオでは、ADO.NET の上位互換性またはアプリケーションの旧バージョンとの互換性に影響を与えるリリース間の変更注意する必要があります。  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>上位互換性と下位互換性  
 上位互換性は、アプリケーションは、.NET Framework の以前のバージョンでコンパイルすることができますが、.NET Framework の以降のバージョンで正常に実行も意味します。 .NET Framework version 1.1 用に記述された ADO.NET コードでは、以降のバージョンとの上位互換性です。  
  
 旧バージョンとの互換性は、アプリケーションは、.NET Framework の新しいバージョンがコンパイルされるが、機能を失うことがなく、.NET Framework の以前のバージョンで引き続き実行を意味します。 もちろん、この操作が、.NET Framework の新しいバージョンで導入された機能の場合です。  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>.NET Framework Data Provider for ODBC  
 バージョン 1.1 では、.NET Framework Data Provider for ODBC (<xref:System.Data.Odbc>) は、.NET Framework の一部として含まれます。 ODBC データ プロバイダーを利用できる .NET Framework バージョン 1.0 の開発者から Web ダウンロードとして、[データ アクセスおよびストレージ デベロッパー センター](https://go.microsoft.com/fwlink/?linkid=4173)します。 ダウンロードした .NET Framework Data Provider for ODBC の名前空間は**Microsoft.Data.Odbc**します。  
  
 .NET Framework version 1.0、ODBC データ プロバイダーを使用して、データ ソースに接続するために開発されたアプリケーションがあり、.NET Framework version 1.1 またはそれ以降のバージョンでそのアプリケーションを実行する場合は、ODBC dat の名前空間を更新する必要があります。プロバイダーを**System.Data.Odbc**します。 する必要がありますを再コンパイルすること、.NET Framework の新しいバージョンの。  
  
 ODBC データ プロバイダーを使用して、データ ソースに接続する .NET Framework バージョン 2.0 以降用に開発されたアプリケーションがあり、.NET Framework version 1.0 でそのアプリケーションを実行する場合、ODBC データ プロバイダーをダウンロードしてインストールする必要があります.NET Framework version 1.0 システム。 必要があります変更する名前空間に ODBC データ プロバイダーの**Microsoft.Data.Odbc**、および .NET Framework version 1.0 用にアプリケーションを再コンパイルします。  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle  
 バージョン 1.1 では、.NET Framework Data Provider for Oracle (<xref:System.Data.OracleClient>) は、.NET Framework の一部として含まれます。 データ プロバイダーを利用できる .NET Framework バージョン 1.0 の開発者から Web ダウンロードとして、[データ アクセスおよびストレージ デベロッパー センター](https://go.microsoft.com/fwlink/?linkid=4173)します。  
  
 データ プロバイダーを使用して、データ ソースに接続する .NET Framework バージョン 2.0 以降用に開発されたアプリケーションがあり、.NET Framework version 1.0 でそのアプリケーションを実行する場合は、データ プロバイダーをダウンロードし、.NE にインストールする必要があります。T Framework version 1.0 システム。  
  
## <a name="code-access-security"></a>コード アクセス セキュリティ  
 .NET Framework version 1.0 で .NET Framework データ プロバイダー (<xref:System.Data.SqlClient>、 <xref:System.Data.OleDb>) FullTrust アクセス許可を持つ実行に必要な。 FullTrust アクセス許可の原因がより少ないゾーンで、.NET Framework データ プロバイダーを .NET Framework version 1.0 を使用すると、<xref:System.Security.SecurityException>します。  
  
 ただし、以降、.NET Framework version 2.0 では、.NET Framework データ プロバイダーをすべて使用できますで部分的に信頼されたゾーン。 さらに、新しいセキュリティ機能は、.NET Framework version 1.1 での .NET Framework データ プロバイダーに追加されました。 この機能により、特定のセキュリティ ゾーンで使用できる接続文字列を制限することができます。 特定のセキュリティ ゾーンに対して空白のパスワードの使用を禁止することもできます。 詳細については、「 [Code Access Security and ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)」を参照してください。  
  
 .NET Framework の各インストールには、個別の Security.config ファイルがあるために、セキュリティ設定と互換性の問題はありません。 ただし、アプリケーションは、ADO.NET .NET Framework version 1.1 に含まれるおよびそれ以降の追加のセキュリティ機能に依存する場合、version 1.0 システムに配布することはできません。  
  
## <a name="sqlcommand-execution"></a>SqlCommand の実行  
 方法は、.NET Framework version 1.1 以降を<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>コマンドを実行、データ ソースが変更されました。  
  
 .NET framework version 1.0、<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>のコンテキストですべてのコマンドを実行、 **sp_executesql**ストアド プロシージャ。 その結果、接続の状態に影響を与えるコマンド (たとえば、SET NOCOUNT ON) は、現在のコマンドの実行だけに適用されます。 接続が開かれている間に実行される後続のコマンドについては、接続の状態は変更されません。  
  
 .NET Framework version 1.1 以降で<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>のみのコンテキストでコマンドを実行、 **sp_executesql**ストアド プロシージャの場合は、コマンドにパラメーター、これにより、パフォーマンスの向上。 その結果、接続の状態に影響を与えるコマンドが、非パラメーター化コマンドに含まれている場合、接続が開いている間に実行される後続のすべてのコマンドに対して、接続の状態を変更します。  
  
 たとえば、<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> への呼び出しで次のバッチ コマンドが実行されるとします。  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 .NET framework version 1.1 以降では、NOCOUNT は、接続が開いている間に実行される後続のコマンドの ON はとどまります。 .NET Framework version 1.0 では、NOCOUNT は、コマンドの現在の実行に対してだけをします。  
  
 この変更は、の動作に依存している場合、アプリケーションの上位および下位の互換性に影響は<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.NET Framework のいずれかのバージョン。  
  
 前と後の両方のバージョンの .NET Framework 上で実行されるアプリケーションでは、動作が実行しているバージョンに関係なく同じであるかどうかを確認するコードを記述することができます。 変更された接続状態が後続のすべてのコマンドでも有効になるようにする場合は、<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> を使用してコマンドを実行することをお勧めします。 変更された接続状態が後続のコマンドでは無効になるようにする場合は、接続状態をリセットするコマンドを含めるようにしてください。 例:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

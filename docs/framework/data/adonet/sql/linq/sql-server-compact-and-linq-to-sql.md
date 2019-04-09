---
title: SQL Server Compact および LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: db3f7aef082d965dc27b69f5a966ff038c0ffac0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145718"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact および LINQ to SQL
SQL Server Compact は、Visual Studio にインストールされている既定のデータベースです。 詳細については、次を参照してください。[を使用して SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))します。  
  
 ここでは、使用量、構成、機能セット、およびスコープの主な相違点の概要について[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]をサポートします。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>LINQ to SQL との関係における SQL Server Compact の特徴  
 既定では、SQL Server Compact のすべての Visual Studio エディションがインストールされている、そのため開発用コンピューターで使用するために使用可能な[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]します。 SQL Server Compact を使用するアプリケーションの展開と[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL Server アプリケーションとは異なります。 SQL Server Compact は .NET Framework の一部ではないため、アプリケーションにパッケージ化するか、Microsoft サイトから個別にダウンロードする必要があります。  
  
 これには、次のような特徴があります。  
  
-   SQL Server Compact は DLL としてパッケージ化されており、データベース ファイル (.sdf 拡張子) に対して直接使用できます。  
  
-   SQL Server Compact は、クライアント アプリケーションと同じプロセスで実行されます。 SQL Server Compact との通信の効率性はそのため、SQL Server と通信するよりも高い。 その一方で、SQL Server Compact はコストを伴うマネージ コードとアンマネージ コード間の相互運用性が必要です。  
  
-   SQL Server Compact DLL のサイズが小さです。 このため、アプリケーション全体のサイズが抑制されます。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムおよび SQLMetal コマンド ライン ツールが SQL Server Compact をサポートしています。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] では、SQL Server Compact はサポートしていません。  
  
## <a name="feature-set"></a>機能セット  
 影響を与える次の方法で、SQL Server Compact の機能セットが SQL Server の機能セットよりはるかに簡単[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]アプリケーション。  
  
-   SQL Server Compact は、ストアド プロシージャまたはビューをサポートしません。  
  
-   SQL Server Compact は、一部のデータ型と SQL 関数のみをサポートします。  
  
-   SQL Server Compact は、一部の SQL コンストラクトのみをサポートします。  
  
-   SQL Server Compact は、最小限のオプティマイザーを備えています。 一部のクエリがタイムアウトになる可能性があることができます。  
  
-   SQL Server Compact は、部分信頼をサポートしません。  
  
## <a name="see-also"></a>関連項目

- [参照](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)

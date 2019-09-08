---
title: SQL Server Compact および LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792540"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact および LINQ to SQL
SQL Server Compact は、Visual Studio と共にインストールされる既定のデータベースです。 詳細については、「 [SQL Server Compact の使用 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))」を参照してください。  
  
 このトピックでは、使用法、構成、機能セット、およびサポート範囲の[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]主な違いについて概説します。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>LINQ to SQL との関係における SQL Server Compact の特徴  
 既定では、すべての Visual Studio エディションに対して SQL Server Compact がインストールされます。したがって、で[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]使用するために開発用コンピューターで使用できます。 ただし、SQL Server Compact を使用するアプリケーションの配置[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]は、SQL Server アプリケーションとは異なります。 SQL Server Compact は .NET Framework の一部ではないため、アプリケーションにパッケージ化するか、Microsoft サイトから個別にダウンロードする必要があります。  
  
 これには、次のような特徴があります。  
  
- SQL Server Compact は DLL としてパッケージ化されており、データベース ファイル (.sdf 拡張子) に対して直接使用できます。  
  
- SQL Server Compact は、クライアントアプリケーションと同じプロセスで実行されます。 そのため、SQL Server Compact との通信効率が SQL Server との通信よりも大幅に高くなる可能性があります。 一方、SQL Server Compact では、マネージコードとアンマネージコードとの間の相互運用性が必要です。  
  
- SQL Server Compact DLL のサイズが小さくなっています。 このため、アプリケーション全体のサイズが抑制されます。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムおよび SQLMetal コマンド ライン ツールが SQL Server Compact をサポートしています。  
  
- オブジェクトリレーショナルデザイナーは SQL Server Compact をサポートしていません。  
  
## <a name="feature-set"></a>機能セット  
 SQL Server Compact 機能セットは、アプリケーションに影響[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]する可能性のある次のような SQL Server の機能セットよりもはるかに簡単です。  
  
- SQL Server Compact は、ストアド プロシージャまたはビューをサポートしません。  
  
- SQL Server Compact は、一部のデータ型と SQL 関数のみをサポートします。  
  
- SQL Server Compact は、一部の SQL コンストラクトのみをサポートします。  
  
- SQL Server Compact は、最小限のオプティマイザーを備えています。 一部のクエリがタイムアウトする可能性があります。  
  
- SQL Server Compact は、部分信頼をサポートしません。  
  
## <a name="see-also"></a>関連項目

- [参照](reference.md)

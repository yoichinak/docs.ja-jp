---
title: SQL Server の CLR 統合の概要
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 76c6fb4cb37807f286f1f1f2aeedbdea6c74fe38
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002146"
---
# <a name="introduction-to-sql-server-clr-integration"></a>SQL Server の CLR 統合の概要
CLR (共通言語ランタイム) は Microsoft .NET Framework の中核部分であり、あらゆる .NET Framework コードに対する実行環境を提供します。 CLR 内で実行されるコードを、マネージド コードと呼びます。 CLR では、JIT (Just-In-Time) コンパイル、メモリの割り当てと管理、タイプ セーフの確保、例外処理、スレッド管理、セキュリティなど、プログラムの実行に必要なさまざまな機能やサービスが提供されます。  
  
 Microsoft SQL Server でホストされる CLR のことを CLR 統合と呼びます。この CLR 統合を使用すると、マネージド コードで、ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、ユーザー定義集計を作成できます。 マネージド コードは実行前にネイティブ コードにコンパイルされるので、シナリオによってはパフォーマンスの大幅な向上を図ることができます。  
  
 マネージド コードは、コード アクセス セキュリティ (CAS)、コード リンク、およびアプリケーション ドメインを使用して、アセンブリが特定の操作を実行することを防止します。 SQL Server は、CAS を使用して、マネージド コードをセキュリティ保護し、オペレーティング システムやデータベース サーバーへの侵害を防止します。  
  
 このセクションは、SQL Server の CLR 統合を利用したプログラミングを始めるのに十分な情報を提供することを目的としており、包括的な情報の提供は目的としていません。 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
- [共通言語ランタイム (CLR) 統合の概要](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>CLR 統合の有効化  
 Microsoft SQL Server では共通言語ランタイム (CLR) 統合機能が既定でオフになっているため、CLR 統合を利用して実装されるオブジェクトを使用するには、CLR 統合機能を有効にする必要があります。 Transact-SQL を使用して CLR 統合を有効にするには、次に示すように、`clr enabled` ストアド プロシージャの `sp_configure` オプションを使用します。  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 `clr enabled` オプションを 0 に設定することにより、CLR 統合を無効にできます。 CLR 統合を無効にすると、SQL Server ではすべての CLR ルーチンの実行が停止され、すべてのアプリケーション ドメインがアンロードされます。  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
- [CLR 統合の有効化](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>CLR アセンブリの配置  
 CLR メソッドをテスト サーバーでテストおよび検証すると、配置スクリプトを使用してこれらを実稼働サーバーに配布できます。 配置スクリプトは手動で生成するか、SQL Server Management Studio を使用して生成することができます。 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
1. [CLR データベースオブジェクトの配置](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>CLR 統合セキュリティ  
 Microsoft SQL Server と Microsoft .NET Framework 共通言語ランタイム (CLR) との統合のセキュリティ モデルは、SQL Server 内部で実行されるさまざまなタイプの CLR オブジェクトおよび非 CLR オブジェクトの間のアクセスを管理し、セキュリティで保護します。 これらのオブジェクトは、Transact-SQL ステートメントまたはサーバーで実行される別の CLR オブジェクトから呼び出される可能性があります。  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
- [CLR 統合のセキュリティ](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>CLR アセンブリのデバッグ  
 Microsoft SQL Server は、データベース内の Transact-SQL オブジェクトおよび共通言語ランタイム (CLR) オブジェクトのデバッグをサポートしています。 デバッグは言語をまたがって機能します。ユーザーは、Transact-SQL から CLR オブジェクトへ、または CLR オブジェクトから Transact-SQL へシームレスにデバッグできます。  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
- [CLR データベースオブジェクトのデバッグ](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>関連項目

- [コード アクセス セキュリティと ADO.NET](../code-access-security.md)
- [ADO.NET の概要](../ado-net-overview.md)

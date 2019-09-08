---
title: SQL Server の共通言語ランタイム統合
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 77b40c6a1576b87d9bb4a7eb4b1ee3df8828b892
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780861"
---
# <a name="sql-server-common-language-runtime-integration"></a>SQL Server の共通言語ランタイム統合
SQL Server 2005 で、Microsoft Windows 用の .NET Framework の共通言語ランタイム (CLR) コンポーネントの統合が導入されました。 つまり、Microsoft Visual Basic .NET や Microsoft Visual C# を含む任意の .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を作成できるようになりました。 マネージド コードが Microsoft SQL Server 環境とデータをやり取りできるように、<xref:Microsoft.SqlServer.Server> 名前空間には新しいアプリケーション プログラミング インターフェイス (API) のセットが含まれています。  
  
 このセクションでは、SQL Server の共通言語ランタイム (CLR) 統合および SQL Server のインプロセス固有の ADO.NET の拡張に固有の機能や動作ついて説明します。  
  
 このセクションは、SQL Server の CLR 統合を利用したプログラミングを始めるのに十分な情報を提供することを目的としており、包括的な情報の提供は目的としていません。 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
1. [共通言語ランタイム (CLR) 統合プログラミングの概念](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server の CLR 統合の概要](introduction-to-sql-server-clr-integration.md)  
 SQL Server の CLR 統合の概要について説明します。 追加情報へのリンクもあります。  
  
 [CLR ユーザー定義関数](clr-user-defined-functions.md)  
 テーブル値関数、スカラー関数、ユーザー定義集計関数など、さまざまな種類の CLR 関数の実装方法と使用方法について説明します。  
  
 [CLR ユーザー定義型](clr-user-defined-types.md)  
 CLR のユーザー定義型を実装して使用する方法について説明します。 追加情報へのリンクもあります。  
  
 [CLR ストアド プロシージャ](clr-stored-procedures.md)  
 CLR のストアド プロシージャを実装して使用する方法について説明します。 追加情報へのリンクもあります。  
  
 [CLR トリガー](clr-triggers.md)  
 CLR のトリガーを実装して使用する方法について説明します。 追加情報へのリンクもあります。  
  
 [コンテキスト接続](the-context-connection.md)  
 コンテキスト接続について説明します。  
  
 [SQL Server のインプロセス固有の ADO.NET の動作](sql-server-in-process-specific-behavior-of-adonet.md)  
 SQL Server のインプロセス固有の ADO.NET の拡張およびコンテキスト接続について説明します。 追加情報へのリンクもあります。  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](index.md)
- [ADO.NET の概要](../ado-net-overview.md)

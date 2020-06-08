---
title: タスク並列ライブラリ (TPL)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 45c9f43e67b66b00758afa0659897971aef317c2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284976"
---
# <a name="task-parallel-library-tpl"></a>タスク並列ライブラリ (TPL)
タスク並列ライブラリ (TPL: Task Parallel Library) は、<xref:System.Threading?displayProperty=nameWithType> 名前空間および <xref:System.Threading.Tasks?displayProperty=nameWithType> 名前空間におけるパブリック型と API のセットです。 TPL の目的は、アプリケーションに並列処理とコンカレンシーを追加するプロセスを簡略化して、開発者の生産性を高めることです。 TPL は、使用可能なすべてのプロセッサを最も効率的に使用するように、コンカレンシーの程度を動的に拡大します。 さらに TPL は、作業のパーティション分割、<xref:System.Threading.ThreadPool> 上のスレッドのスケジュール、キャンセルのサポート、状態管理、および他の低水準の詳細を処理します。 TPL を使用すると、コードのパフォーマンスが大幅に向上し、目的を達成するためのプログラミング作業に集中できます。  
  
 .NET Framework 4 以降では、マルチスレッド コードおよび並列コードを作成する際に TPL を使用することをお勧めします。 ただし、すべてのコードが並列化に適している訳ではありません。ループの各反復処理で少量の作業のみを実行する場合、または多数の反復処理のために実行しない場合、並列化のオーバーヘッドによってコードの実行が遅くなる可能性があります。 さらに、マルチスレッド コードのような並列化によって、プログラムの実行がより複雑になります。 TPL はマルチスレッドのシナリオを簡略化しますが、たとえばロック、デッドロックおよび競合状態のスレッド処理の基本的な概念を理解し、TPL を効率的に使用することをお勧めします。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-|-|  
|[データの並列化](data-parallelism-task-parallel-library.md)|並列の `for` ループおよび `foreach` ループ (Visual Basic では `For` および `For Each`) を作成する方法について説明します。|  
|[タスク ベースの非同期プログラミング](task-based-asynchronous-programming.md)|<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> を使用して暗黙的にタスクを作成および実行する方法、または <xref:System.Threading.Tasks.Task> オブジェクトを直接使用して明示的にタスクを作成および実行する方法について説明します。|  
|[データフロー](dataflow-task-parallel-library.md)|相互に非同期通信を行う必要がある複数の操作を処理する場合、またはデータが使用可能になったときにデータを処理する場合に、TPL データ フロー ライブラリのデータ フロー コンポーネントを使用する方法について説明します。|  
|[TPL と他の非同期パターンの使用](using-tpl-with-other-asynchronous-patterns.md)|TPL と他の非同期パターンを .NET で使用する方法について説明します。|  
|[データとタスクの並列化における注意点](potential-pitfalls-in-data-and-task-parallelism.md)|一般的な落とし穴とその回避方法について説明します。|  
|[Parallel LINQ (PLINQ)](introduction-to-plinq.md)|LINQ クエリでデータの並列化を達成する方法について説明します。|  
|[並列プログラミング](index.md)|.NET 並列プログラミングのトップ レベル ノード。|  
  
## <a name="see-also"></a>関連項目

- [.NET Core および .NET Standard による並列プログラミングのサンプル](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)

---
title: スレッドの使用とスレッド処理
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 863fa565f7c107214273912a6d110b7664bffe6b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131496"
---
# <a name="using-threads-and-threading"></a>スレッドの使用とスレッド処理

.NET では、複数の操作を同時に実行するアプリケーションを記述できます。 他の操作を止める可能性がある操作は個別のスレッドで実行できます。これは*マルチスレッド*や*フリー スレッド*と呼ばれているプロセスです。  
  
マルチスレッドを利用するアプリケーションはユーザーの入力に対する応答性が良くなります。プロセッサを集中的に利用するタスクが個別のスレッドで実行されるため、ユーザー インターフェイスの動作が妨げられません。 マルチスレッドはまた、スケーラブルなアプリケーションの開発にも便利です。ワークロードが増えたとき、スレッドを追加できるからです。

> [!NOTE]
> アプリケーションのスレッドの動作をさらに細かく制御するには、スレッドを自分で管理します。 しかし、.NET Framework 4 以降では、<xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> クラスおよび <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラス、[Parallel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=nameWithType> 名前空間の新しい同時実行コレクション クラス、スレッドではなくタスクの概念を基にした新しいプログラミング モデルにより、マルチスレッド プログラミングが大幅に簡略化されています。 詳細については、「[.NET での並列プログラミング](../parallel-programming/index.md)」と「[タスク並列ライブラリ (TPL)](../parallel-programming/task-parallel-library-tpl.md)」を参照してください。

## <a name="how-to-create-and-start-a-new-thread"></a>方法: 新しいスレッドを作成して開始する

<xref:System.Threading.Thread?displayProperty=nameWithType> クラスの新しいインスタンスを作成し、コンストラクターに対して新しいスレッドで実行するメソッド名を指定して、新しいスレッドを作成します。 作成したスレッドを開始するには、<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> メソッドを呼び出します。 詳細と例については、「[スレッドを作成し、開始時にデータを渡す](creating-threads-and-passing-data-at-start-time.md)」の記事と <xref:System.Threading.Thread> API リファレンスを参照してください。

## <a name="how-to-stop-a-thread"></a>方法: スレッドを停止する

スレッドの実行を終了するには、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> メソッドを使用します。 このメソッドでは、呼び出されたスレッド上で <xref:System.Threading.ThreadAbortException> が生成されます。 詳細については、「[スレッドの破棄](destroying-threads.md)」を参照してください。

.NET Framework 4 以降、<xref:System.Threading.CancellationToken?displayProperty=nameWithType> を使用してスレッドを協調的にキャンセルできます。 詳細については、「[マネージド スレッドのキャンセル](cancellation-in-managed-threads.md)」を参照してください。

<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> メソッドを使用すると、そのメソッドが呼び出されたスレッドが終了するまで呼び出し元のスレッドを待機させるようにすることができます。

## <a name="how-to-pause-or-interrupt-a-thread"></a>方法: スレッドを一時停止または中断する

<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> メソッドを使用して、現在のスレッドを指定した時間一時停止します。 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> メソッドを呼び出すことによって、ブロックされたスレッドを中断できます。 詳細については、「[スレッドの一時中断と再開](pausing-and-resuming-threads.md)」を参照してください。

## <a name="thread-properties"></a>スレッド プロパティ

<xref:System.Threading.Thread> プロパティの一部を次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|スレッドが起動していて、正常終了しておらず中止されてもいない場合は、`true` が返されます。|  
|<xref:System.Threading.Thread.IsBackground%2A>|スレッドがバックグラウンド スレッドかどうかを示すブール値を取得または設定します。 バックグラウンド スレッドはフォアグラウンド スレッドに似ていますが、プロセスの停止を防ぐことはありません。 あるプロセスに属するフォアグラウンド スレッドがすべて停止すると、共通言語ランタイムは、アライブ状態のバックグラウンド スレッドで <xref:System.Threading.Thread.Abort%2A> メソッドを呼び出し、プロセスを終了します。 詳細については、「[フォアグラウンド スレッドとバックグラウンド スレッド](foreground-and-background-threads.md)」を参照してください。|  
|<xref:System.Threading.Thread.Name%2A>|スレッドの名前を取得または設定します。 デバッグ時、個々のスレッドを検出するために頻繁に使用されます。|  
|<xref:System.Threading.Thread.Priority%2A>|オペレーティング システムがスレッド スケジュールに優先順位を設定するために使用する <xref:System.Threading.ThreadPriority> 値を取得または設定します。 詳細については、「[スレッドのスケジューリング](scheduling-threads.md)」と <xref:System.Threading.ThreadPriority> リファレンスを参照してください。|  
|<xref:System.Threading.Thread.ThreadState%2A>|スレッドの現在の状態を示す <xref:System.Threading.ThreadState> 値を取得します。|  

## <a name="see-also"></a>関連項目

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [スレッドおよびスレッド処理](threads-and-threading.md)
- [並列プログラミング](../parallel-programming/index.md)

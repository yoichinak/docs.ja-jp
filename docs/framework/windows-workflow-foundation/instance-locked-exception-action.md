---
title: インスタンス ロック例外アクション
ms.date: 03/30/2017
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
ms.openlocfilehash: 0cb39c51436271999c66c30210e0da79adc92e72
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699540"
---
# <a name="instance-locked-exception-action"></a>インスタンス ロック例外アクション
SQL Workflow Instance Store の <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> プロパティでは、SQL 永続化プロバイダーが <xref:System.Runtime.DurableInstancing.InstanceLockedException> を受け取ったときに実行するアクションを指定します。 永続化プロバイダーがこの例外を受け取るのは、別のサービス ホストが現在ロックしているワークフロー サービス インスタンスをこの永続化プロバイダーがロックしようとしたときです。 このプロパティの値は <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>、<xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>、および <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> です。 既定値は <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> です。 この 3 つのオプションを次の一覧で説明します。  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>。 サービス ホストがワークフロー サービス インスタンスを渡しますのロックを試行しません、<xref:System.Runtime.DurableInstancing.InstanceLockedException>呼び出し元にします。  場合は、ワークフローは 60 秒を超える期間をメモリ内に保持を使用して、<xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>再試行します。 既定値は <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> です。  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>。 サービス ホストは一定の再試行間隔でワークフロー サービス インスタンスのロックを再試行し、シーケンスの最後に <xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。 ワークフローがおよそ 5 ～ 60 秒間メモリに留まり、ワークフローをアンロードする前にすべてのメッセージを処理するため、同じホスト上の同じインスタンスに送信されるメッセージのようにメッセージがバッチで届く場合、リソースを無駄にしない最適な待ち時間を実現するため <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> を使用します。  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>。 サービス ホストは指数バックオフ間隔でワークフロー サービス インスタンスのロックを再試行し、シーケンスの最後に例外を呼び出し元に渡します。 ワーク フローがとても短い間 (5 秒以内) 目盛りに留まる場合、または Web ファームが大きく別のメッセージが同じホストに渡される可能性が高くない場合、最適な待ち時間を実現するため <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> を使用します。  
  
 インスタンス ロック例外アクション機能は、次のシナリオをサポートしています。 いずれのシナリオでも、SqlWorkflowInstanceStore の instanceLockedExceptionAction プロパティが <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> または <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> に設定されていれば、ホストはインスタンスのロックを取得するために、再試行を自動的に繰り返します。  
  
1. **正常なシャット ダウンを有効にして、アプリケーション ドメインの重複したリサイクルします。** たとえば、 **AppDomain**サービス ホストを持つワークフロー サービス インスタンスを実行しているがされているリサイクルされると、新しい**AppDomain**が、古いで新しい要求を処理するために呼び出された**AppDomain**正常に停止されます。 このシャットダウンは、ワークフロー サービス インスタンスがアイドル状態になるまで待機した後、このインスタンスを永続化してアンロードします。 しようとすると、新しいホストによって**AppDomain**インスタンスをロックすると、<xref:System.Runtime.DurableInstancing.InstanceLockedException>します。  
  
2. **同種サーバー ファームで、永続的なワークフローを水平的スケーリングします。** ワークフロー インスタンスが実行されているサーバー ファームのノードがクラッシュし、ワークフロー ホストが実行しているインスタンスのロックを解除できないことを想定しています。 ファームの別のノードで実行されているサービス ホストは、そのワークフロー インスタンスのメッセージを受け取ると、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を受け取ることになる、これらのインスタンスのロックを取得する処理を試行します。 ロックを更新することになっていたホストは存在しないため、ロックはしばらくすると期限切れになります。  
  
     **同種サーバー ファームで、永続的なワークフローを水平的スケーリングします。**  NLB (ネットワーク ロード バランサー) の背後にある複数のホストを使用して永続的なワークフローを水平方向にスケーリングするとに、インスタンスには、次のメッセージがルーティングされます、ファームの 1 つのノードで実行されているワークフロー ホストを選択し、ワークフロー インスタンスを読み込みますが、メッセージを処理しますNLB には、インスタンスを既に実行されているホストにメッセージを配信するルーティング アルゴリズムがあるないために、別のノードで実行されているホスト。 メッセージを受け取ると、最初のホストがワークフロー インスタンスのロックを保持しているため、2 つ目のホストがこのインスタンスをロードする処理を試行し、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を受け取ります。 最初のホストは、最初のメッセージの処理を完了してロック解除が行われるときにこのインスタンスのロックを解除し、2 つ目のホストは、次に再試行を行い、インスタンスをロードして、2 つ目のメッセージを処理するときにロックを取得します。

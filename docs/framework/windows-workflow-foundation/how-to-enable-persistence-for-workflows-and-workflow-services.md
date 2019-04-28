---
title: '方法: ワークフローとワークフロー サービスの永続化を有効にする'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761430"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>方法: ワークフローとワークフロー サービスの永続化を有効にする
ここでは、ワークフローとワークフロー サービスの永続化を有効にする方法について説明します。  
  
## <a name="enable-persistence-for-workflows"></a>ワークフローの永続化を有効にする  
 使用して、インスタンス ストアを関連付けることができます、 **WorkflowApplication**を使用して、<xref:System.Activities.WorkflowApplication.InstanceStore%2A>のプロパティ、<xref:System.Activities.WorkflowApplication>クラス。 <xref:System.Activities.WorkflowApplication.Persist%2A> メソッドは、アプリケーションに関連付けられたインスタンス ストアにワークフローを保存または永続化します。 <xref:System.Activities.WorkflowApplication.Unload%2A> メソッドは、ワークフローをインスタンス ストアに永続化し、メモリからインスタンスをアンロードします。 **ロード**メソッドは、インスタンスの永続化ストアに格納されているワークフロー データを使用してメモリにワークフローを読み込みます。  
  
 **Persist**メソッドは、次の手順を実行します。  
  
1. ワークフローのスケジューラを一時停止し、アイドル状態に移行するまで待機します。  
  
2. ワークフローを永続化 (永続化ストアに保存) します。  
  
3. ワークフローのスケジューラを再開します。  
  
 **アンロード**メソッドは、次の手順を実行します。  
  
1. ワークフローのスケジューラを一時停止し、アイドル状態に移行するまで待機します。  
  
2. ワークフローを永続化 (永続化ストアに保存) します。  
  
3. メモリ内のワークフロー インスタンスを破棄します。  
  
 両方の**Persist**と**アンロード**メソッドは、ワークフローが非永続化ゾーンを終了するまでに、ワークフローが非永続化ゾーンではブロックされます。 メソッドは、非永続化ゾーンの完了後に、永続化またはアンロードの操作を続行します。 期限切れになる前に非永続化ゾーンが完了しない場合、または永続化プロセスに時間がかかりすぎる場合は、TimeoutException がスローされます。  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>コードでのワークフロー サービスの永続化を有効にする  
 **DurableInstancingOptions**のメンバー、<xref:System.ServiceModel.WorkflowServiceHost>クラスという名前のプロパティには**InstanceStore**に関連付ける、インスタンス ストアを使用できる、 **WorkflowServiceHost**.  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 ときに、 **WorkflowServiceHost**が開かれると、永続化は自動的に有効になっている場合、 **DurableInstancingOptions.InstanceStore**が null でないです。  
  
 通常、サービスの動作を使用して、ワークフロー サービス ホストで使用する具象インスタンス ストアを提供します。、 **InstanceStore**プロパティ。 たとえば、SqlWorkflowInstanceStoreBehavior のインスタンスを作成、 **SqlWorkflowInstanceStore**、構成、およびに割り当てます、 **DurableInstancingOptions.InstanceStore**します。  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>アプリケーション構成ファイルを使用してワークフロー サービスの永続化を有効にする  
 次のコードを app.config または web.config file に追加すると、アプリケーション構成ファイルを使用して永続化を有効にできます。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```

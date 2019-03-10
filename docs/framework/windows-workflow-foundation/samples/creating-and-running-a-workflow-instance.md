---
title: ワークフロー インスタンスの作成と実行
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d0c59946b6419e7088e3426d7ddd08537cfab5a4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722010"
---
# <a name="creating-and-running-a-workflow-instance"></a>ワークフロー インスタンスの作成と実行
このサンプルでは、ワークフロー インスタンスを実行する方法を示します。 ここでは、ワークフロー インスタンスを同期的または非同期的に実行する方法を示します。  
  
## <a name="demonstrates"></a>使用例  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>説明  
 サンプルの最初の部分では <xref:System.Activities.WorkflowInvoker.Invoke%2A> を使用します。 これはワークフローを実行する最も基本的な方法です。 <xref:System.Activities.WorkflowInvoker.Invoke%2A> を使用して実行するワークフローは同期的に実行されます。  
  
 サンプルの 2 番目の部分は <xref:System.Activities.WorkflowApplication> クラスを使用します。 <xref:System.Activities.WorkflowApplication> を使用すると、各インスタンスをより細かく制御できるようになり、実行中のワークフローと対話したり、ワークフローを非同期的に実行したりできます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>関連項目
- [WorkflowInvoker と WorkflowApplication の使用](../using-workflowinvoker-and-workflowapplication.md)

---
title: インスタンスのアクティブ化処理
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 088722ba19a1f38e8a341e34a8344963021f1113
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584923"
---
# <a name="instance-activation"></a>インスタンスのアクティブ化処理
SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なワークフロー インスタンスを永続性データベースで検出します。 このタスクは、実行可能なワークフロー インスタンスを検出すると、このインスタンスをアクティブ化することができるワークフロー ホストに通知します。 Instance Store がアクティブ化可能なワークフロー インスタンスを検出した場合、ワークフロー ホストをアクティブ化する汎用ホストに Instance Store が通知を行い、ワークフロー ホストがワークフロー インスタンスを実行します。 このトピックの以降のセクションでは、インスタンスのアクティブ化処理を詳細に説明します。  
  
## <a name="RunnableSection"></a> 検出と実行可能なワークフロー インスタンスをアクティブ化  
 SQL Workflow Instance Store がワークフロー インスタンスと見なします*実行可能な*インスタンスが中断状態または完了状態にないし、次の条件を満たす場合。  
  
- インスタンスがロック解除されていて、保留タイマーの期限が切れている。  
  
- インスタンスに期限切れのロックがある。  
  
- インスタンスのロックが解除され、状態が**Executing**します。  
  
 SQL Workflow Instance Store は、実行可能なインスタンスを見つけると <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> を生成します。 その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> に定期受信し、インスタンスの読み込みが可能なワークフロー ホストは、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> を実行してインスタンスをメモリに読み込みます。 ワークフロー ホストは、ホストとインスタンスは、メタデータ プロパティを持っている場合は、ワークフロー インスタンスを読み込むことができると見なされます**WorkflowServiceType**同じ値に設定します。  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>アクティブ化可能なワークフロー インスタンスの検出とアクティブ化  
 ワークフロー インスタンスと見なされます*アクティブ化可能な*コンピューターでは、インスタンスを読み込むことができるワークフロー ホストが実行されていないインスタンスが実行可能な場合は、します。 実行可能なワークフロー インスタンスの定義については、前の「実行可能なワークフロー インスタンスの検出とアクティブ化」を参照してください。  
  
 SQL Workflow Instance Store は、データベースでアクティブ化可能なワークフロー インスタンスを見つけると <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> を生成します。 その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> に定期受信している汎用ホストは、イベントを受け取ると、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> を実行して、ワークフロー ホストの作成に必要なアクティブ化のパラメーターを取得します。 汎用ホストは、このアクティブ化パラメーターを使用してワークフロー ホストを作成します。作成されたワークフロー ホストは、実行可能なサービス インスタンスを読み込んで実行します。  
  
## <a name="generic-hosts"></a>汎用ホスト  
 汎用ホストは、メタデータ プロパティの値を持つホスト**WorkflowServiceType**汎用ホストに設定されて**WorkflowServiceType.Any**を任意のワークフロー型を処理できることを示します。 汎用ホストがという XName パラメーター **ActivationType**します。  
  
 現在、SQL Workflow Instance Store には、汎用ホストに設定、ActivationType パラメーターの値をサポートしています。 **WAS**します。 ActivationType が WAS に設定されていない場合、SQL Workflow Instance Store は <xref:System.Runtime.DurableInstancing.InstancePersistenceException> をスローします。 付属するワークフロー管理サービス、[!INCLUDE[dublin](../../../includes/dublin-md.md)]に設定されたアクティブ化型を持つ汎用ホスト**WAS**します。  
  
 WAS アクティブ化の場合、汎用ホストは、新しいホストをアクティブ化できるエンドポイント アドレスを派生する一連のアクティブ化パラメーターを要求します。 WAS アクティブ化のアクティブ化パラメーターは、サイトの名前、サイトを基準としたアプリケーションの相対パス、アプリケーションを基準としたサービスの相対パスです。 SQL Workflow Instance Store は、<xref:System.Activities.DurableInstancing.SaveWorkflowCommand> の実行中にこれらのアクティブ化パラメーターを格納します。  
  
## <a name="runnable-instances-detection-period"></a>実行可能インスタンス検出期間  
 **実行可能インスタンス検出期間**SQL Workflow Instance Store のプロパティは、SQL Workflow Instance Store が実行可能またはアクティブ化可能なワークフローを検出するために検出タスクを実行するまでの期間を指定します前の検出サイクルの後に、永続性データベースのインスタンス。 参照してください[実行可能インスタンス検出期間](runnable-instances-detection-period.md)このプロパティの詳細についてはします。

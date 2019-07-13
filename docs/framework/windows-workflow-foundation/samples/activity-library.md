---
title: アクティビティ ライブラリ
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: b701d382c25644181b23f3c0f0cd8e019b8d37d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909182"
---
# <a name="activity-library"></a>アクティビティ ライブラリ
このセクションには、高度なカスタム アクティビティでは、Windows Workflow Foundation (WF) を示すサンプルが含まれています。  
  
## <a name="in-this-section"></a>このセクションの内容

 [SendMail カスタム アクティビティ](sendmail-custom-activity.md)  
 <xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。  
  
 [制限された並列 ForEach](throttled-parallel-foreach.md)  
 `ThrottleParallelForEach` アクティビティは、実行するコンカレンシー分岐の数を制限するためのコンカレンシー要因を設定できるという 1 つの例外を除き、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティと似ていることについて示します。
  
 [データベース アクセス アクティビティ](database-access-activities.md)  
 取得、情報を変更または使用するデータベースへのアクセスを許可するアクティビティを作成する方法を示します[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)データベースにアクセスします。  
  
 [.NET Framework 4.5 の外部化されたポリシー アクティビティ](externalized-policy-activity-in-net-framework-4-5.md)  
 ExternalizedPolicy4 アクティビティにより、既存の Windows Workflow Foundation での実行方法を示します[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)](WF 3.5)<xref:System.Workflow.Activities.Rules.RuleSet>オブジェクトの Windows Workflow Foundation の[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)](WF 4.5) 直接を使用して、ルール エンジンはWF 3.5 に付属しています。 
  
 [非ジェネリックの ForEach](non-generic-foreach.md)  
 <xref:System.Activities.Statements.ForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。  
  
 [非ジェネリックの ParallelForEach](non-generic-parallelforeach.md)  
 <xref:System.Activities.Statements.ParallelForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。  
  
 [WorkflowInstanceId の取得](get-workflowinstanceid.md)  
 カスタム アクティビティ `GetWorkflowInstanceId` を使用して、ワークフロー インスタンス ID を返す方法を示します。

---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: db5e1083c07d4e204eb19eaae9257ed44439132e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206565"
---
# <a name="workflowruntime"></a>\<workflowRuntime>
インスタンスの設定を指定<xref:System.Workflow.Runtime.WorkflowRuntime>ワークフロー ベースの Windows Communication Foundation (WCF) サービスをホストするためです。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<workflowRuntime>  
  
## <a name="syntax"></a>構文  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|cachedInstanceExpiration|ワークフロー インスタンスが強制的にアンロードまたは中止される前に、アイドル状態でメモリに残ることができる最大期間を指定する、省略可能な <xref:System.TimeSpan> 値。 unloadOnIdle を実行する `PersistenceService` が workflowruntime に設定されている場合、この属性は無視されます。|  
|enablePerformanceCounters|パフォーマンス カウンターが有効であるかどうかを指定する省略可能なブール値。 パフォーマンス カウンターは、ワークフローに関連したさまざまな統計情報を提供します。ただしそのために、ワークフロー ランタイム エンジンが起動してワークフロー インスタンスが実行されている間は、パフォーマンスが低下します。 既定値は `true` です。|  
|name|ワークフロー ランタイム エンジンの名前を含む文字列。 名前は出力で使用され、このランタイムを、システムで実行されている他のランタイム (パフォーマンス カウンターなど) と区別するために使用されます。<br /><br /> 既定値は空の文字列です。|  
|validateOnCreate|WorkflowServiceHost を開いたときにワークフロー定義の検証を行うかどうかを指定する省略可能なブール値。  この属性が `true` に設定されているときは、`WorkflowServiceHost.Open` が呼び出されるたびにワークフローの検証が実行されます。 検証エラーが見つかった場合は、<xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> エラーがスローされます。<br /><br /> このプロパティが `false` に設定されている場合、ワークフロー定義の検証は行われません。<br /><br /> このプロパティの既定値は `true` です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|commonParameters|サービスによって使用される共通パラメーターのコレクション。 このコレクションには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。|  
|サービス|<xref:System.Workflow.Runtime.WorkflowRuntime> エンジンに追加されるサービスのコレクション。 要素は、<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 型です。  コレクションで指定されたサービスはワークフロー ランタイム エンジンによって初期化され、適切な <xref:System.Workflow.Runtime.WorkflowRuntime> コンストラクターが呼び出されるとワークフロー ランタイム エンジンのサービスに追加されます。 したがって、コレクションで指定されたサービスは、そのコンストラクターのシグネチャに関して一定の規則に従う必要があります。 詳細については、「<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>」を参照してください。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 動作を制御する構成ファイルの使用の詳細については、<xref:System.Workflow.Runtime.WorkflowRuntime>オブジェクトの Windows Workflow Foundation ホスト アプリケーションでは、次を参照してください。[ワークフロー構成ファイル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))します。  
  
## <a name="example"></a>例  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [ワークフロー構成ファイル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))

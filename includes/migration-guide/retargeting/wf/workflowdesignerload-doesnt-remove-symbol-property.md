---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774488"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load ではシンボル プロパティが削除されない

|   |   |
|---|---|
|説明|ワークフロー デザイナーで .NET Framework 4.5 を対象とし、再ホストされた 3.5 ワークフローを <xref:System.Activities.Presentation.WorkflowDesigner.Load> メソッドで読み込むと、ワークフローの保存中に <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> がスローされます。|
|提案される解決策|このバグは、ワークフロー デザイナーで .NET Framework 4.5 を対象とするときにのみ現れるため、<code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> を 4.0 の .NET Framework に設定することによって回避できます。あるいは、<xref:System.Activities.Presentation.WorkflowDesigner.Load> の代わりに <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> メソッドを使用してワークフローを読み込むことで問題を回避できます。|
|スコープ|Major|
|バージョン|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

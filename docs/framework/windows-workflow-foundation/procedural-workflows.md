---
title: 手続き型ワークフロー
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 15ff155fb057c4c10663d383a8942108c6e4375c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348369"
---
# <a name="procedural-workflows"></a>手続き型ワークフロー
手続き型ワークフローでは、手続き型言語と似たフロー制御方法を使用します。 これらの構造には `While` と `If` が含まれます。 これらのワークフローは、<xref:System.Activities.Statements.Flowchart> や <xref:System.Activities.Statements.Sequence> など、他のフロー制御アクティビティを使用して自由に構成できます。  
  
## <a name="controlling-execution-flow"></a>実行フローの制御  
 ワークフロー アクティビティ ライブラリには、手続き型言語で使用されるほとんどのフロー制御方法をモデル化するアクティビティがあります。 不足している機能には次が含まれます。  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 フロー制御アクティビティを使用するドラッグ アンド ドロップしてから、**アクティビティ**ツールボックス、デザイナー ウィンドウ内の複合アクティビティ。  
  
> [!NOTE]
>  ワークフローをホストする Windows Server AppFabric のホスティング機能を使用して、Web ファームでは、AppFabric が複数の AppFabric サーバー間でインスタンスを移動します。 この機能を利用するには、リソースがすべてのノード間で共有可能になっている必要があります。  既定の NET 4 ワークフロー アクティビティには、ローカル リソースにアクセスする操作は含まれていません。 AppFabric には特定のワークフローを不変に設定するメカニズムがないため、ワークフローが移動されるとエラーが発生するようなカスタム アクティビティは絶対に作成しないでください。  
  
## <a name="see-also"></a>関連項目

- [Flowchart のワークフロー](flowchart-workflows.md)

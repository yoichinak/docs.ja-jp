---
title: WF のステート マシン アクティビティ
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 64af2698c878066464e2ca3f32d4522d99999aec
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378048"
---
# <a name="state-machine-activities-in-wf"></a>WF のステート マシン アクティビティ
.NET framework 4.5 は、ステート マシン ワークフローを作成するためのいくつかのシステム標準アクティビティおよびアクティビティ デザイナーを提供します。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使い慣れたステート マシン パラダイムを使用して、含まれているアクティビティを実行します。|  
|<xref:System.Activities.Statements.State>|ステート マシンの状態を表します。|  
|<xref:System.Activities.Core.Presentation.FinalState>|ステート マシンの最終状態を表します。 <xref:System.Activities.Core.Presentation.FinalState> は、使用すると、最終状態として事前に構成済みの <xref:System.Activities.Statements.State> を作成するアクティビティ デザイナーです。 詳細については、次を参照してください。 [FinalState アクティビティ デザイナー](/visualstudio/workflow-designer/finalstate-activity-designer)します。|  
|<xref:System.Activities.Statements.Transition>|2 つの状態間の遷移を表します。 ない**ツールボックス**項目<xref:System.Activities.Statements.Transition>ドラッグして行を削除する 2 つの状態遷移をワークフロー デザイナーで作成するまたは、ときに表示される三角形で状態をドロップして 1 つの状態が置かれている別. 詳細については、次を参照してください。 [Transition アクティビティ デザイナー](/visualstudio/workflow-designer/transition-activity-designer)します。|  
  
## <a name="see-also"></a>関連項目

- [チュートリアル入門](getting-started-tutorial.md)

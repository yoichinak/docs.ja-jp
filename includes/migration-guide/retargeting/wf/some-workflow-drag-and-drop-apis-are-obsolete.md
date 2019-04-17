---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234760"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>一部の WorkFlow ドラッグ アンド ドロップ API が廃止されました

|   |   |
|---|---|
|説明|この WorkFlow ドラッグ アンド ドロップ API は廃止され、アプリが 4.5 向けにリビルドされた場合、コンパイラ警告が発生します。|
|提案される解決策|複数オブジェクトでの操作をサポートする新しい <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> API を代わりに使用する必要があります。 または、ビルド警告を抑制するか、古いコンパイラを使用して警告を回避できます。 API は、まだサポートされています。|
|スコープ|マイナー|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|

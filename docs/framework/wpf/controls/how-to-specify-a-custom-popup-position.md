---
title: '方法: ポップアップのカスタム位置を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 2ffba3d1a0fee236f803dd5877d541084192418b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358484"
---
# <a name="how-to-specify-a-custom-popup-position"></a>方法: ポップアップのカスタム位置を指定する
この例のカスタム位置を指定する方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>タイミングを制御、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されて<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>します。  
  
## <a name="example"></a>例  
 ときに、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されて<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>、<xref:System.Windows.Controls.Primitives.Popup>の定義済みのインスタンスを呼び出し、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>を委任します。 このデリゲートは、ターゲット領域の左上隅との左上隅に対して相対的である可能性のあるポイントのセットを返します、<xref:System.Windows.Controls.Primitives.Popup>します。 <xref:System.Windows.Controls.Primitives.Popup>最適な可視性を提供する時点で配置が発生します。  
  
 次の例の位置を定義する方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>を設定して、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>します。 作成して割り当てる方法も示します、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>デリゲートを配置するために、<xref:System.Windows.Controls.Primitives.Popup>します。  2 つのコールバック デリゲートを返します<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>オブジェクト。  場合、<xref:System.Windows.Controls.Primitives.Popup>は、最初の位置にある画面の端で非表示、<xref:System.Windows.Controls.Primitives.Popup>が 2 番目の位置に配置されます。  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 サンプル全体については、次を参照してください。[ポップアップの配置のサンプル](https://go.microsoft.com/fwlink/?LinkID=160032)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.Primitives.Popup>
- [ポップアップの概要](popup-overview.md)
- [方法トピック](popup-how-to-topics.md)

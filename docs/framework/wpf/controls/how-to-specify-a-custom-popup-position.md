---
title: '方法 : ポップアップのカスタム位置を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635748"
---
# <a name="how-to-specify-a-custom-popup-position"></a>方法 : ポップアップのカスタム位置を指定する
この例では、プロパティが に設定されているときに<xref:System.Windows.Controls.Primitives.Popup>、コントロールの<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>カスタム位置を指定<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>する方法を示します。  
  
## <a name="example"></a>例  
 プロパティが<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>に<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>設定されている場合、<xref:System.Windows.Controls.Primitives.Popup>デリゲートの定義済みインスタンスが<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>呼び出されます。 このデリゲートは、ターゲット領域の左上隅と の左上隅を基準にした、指定できるポイントのセットを返します<xref:System.Windows.Controls.Primitives.Popup>。 配置<xref:System.Windows.Controls.Primitives.Popup>は、最適な可視性を提供するポイントで行われます。  
  
 プロパティを に設定して、 の<xref:System.Windows.Controls.Primitives.Popup>位置を定義する方法<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>を次<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>の例に示します。 また、 デリゲートを作成して割り<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>当てる方法も示しています<xref:System.Windows.Controls.Primitives.Popup>。  コールバック デリゲートは<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>2 つのオブジェクトを返します。  が最初<xref:System.Windows.Controls.Primitives.Popup>の位置の画面エッジによって隠されている場合、は<xref:System.Windows.Controls.Primitives.Popup>2 番目の位置に配置されます。  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 完全なサンプルについては、「[ポップアップ配置のサンプル](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Primitives.Popup>
- [ポップアップの概要](popup-overview.md)
- [ハウツー記事](popup-how-to-topics.md)

---
title: '方法: SystemParameters を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 344fb54b48bcbf188b36a29d8205c21deff713c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001456"
---
# <a name="how-to-use-systemparameters"></a>方法: SystemParameters を使用する
この例のプロパティを使用してアクセスする方法を示しています。<xref:System.Windows.SystemParameters>のスタイル設定やボタンをカスタマイズするためにします。  
  
## <a name="example"></a>例  
 システム リソースは、システム設定と一貫性のあるビジュアルを作成できるようにするために、いくつかのシステムに基づく設定をリソースとして公開します。 <xref:System.Windows.SystemParameters> システム パラメーター値のプロパティと値にバインドされるリソース キーの両方を含むクラスです。 たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>は、<xref:System.Windows.SystemParameters>プロパティの値と<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>対応するリソース キーは、します。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のメンバーを使用する<xref:System.Windows.SystemParameters>として静的プロパティの使用状況、または (キーとして静的プロパティの値) を含む動的リソース参照のいずれか。 アプリケーションの実行時にシステムに基づく値を自動的に更新する場合は、動的リソース参照を使用します。それ以外の場合は、静的参照を使用します。 リソース キーがサフィックスが付いて`Key`プロパティ名に追加されます。  
  
 次の例は、アクセスしての静的な値を使用する方法を示しています。<xref:System.Windows.SystemParameters>のスタイル設定やボタンをカスタマイズします。 このマークアップの例ボタンのサイズを適用することで<xref:System.Windows.SystemParameters>をボタンの値。  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 値を使用する<xref:System.Windows.SystemParameters>コードでは、静的参照または動的リソース参照を使用する必要はありません。 値の代わりに、使用、<xref:System.Windows.SystemParameters>クラス。 キー以外のプロパティは、実行時の動作に、静的プロパティとして定義[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]システムでホストされたはリアルタイムでプロパティが再評価されが正しく - ユーザー駆動型のシステム値に対する変更を反映します。 次の例を使用して、ボタンの高さと幅を設定する方法を示しています。<xref:System.Windows.SystemParameters>値。  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.SystemParameters>
- [システム ブラシで領域を塗りつぶす](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemFonts を使用する](how-to-use-systemfonts.md)
- [システム パラメーター キーを使用する](how-to-use-system-parameters-keys.md)
- [方法トピック](resources-how-to-topics.md)

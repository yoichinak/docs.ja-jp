---
title: '方法: PriorityBinding を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: cf21041a7f3d5b75803378cf05768ee6f1008fdd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354597"
---
# <a name="how-to-implement-prioritybinding"></a>方法: PriorityBinding を実装する
<xref:System.Windows.Data.PriorityBinding> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]のバインディングの一覧を指定することによって動作します。 バインディングのリストの順序は、最も高い優先度から最も低い優先順位。 最高の優先度のバインドは、値を返す場合が正常に処理されるときはありますありません、リスト内の他のバインディングを処理する必要が。 最高の優先度のバインドを評価する時間がかかる場合がある可能性がありますの優先順位の高いバインドが正常に値を返すまで正常に値を返す次の最も高い優先順位が使用されます。  
  
## <a name="example"></a>例  
 示すためにどの<xref:System.Windows.Data.PriorityBinding>、動作、`AsyncDataSource`プロパティは、次の 3 つのオブジェクトが作成された: `FastDP`、`SlowerDP`と`SlowestDP`。  
  
 Get アクセサー`FastDP`の値を返します、`_fastDP`データ メンバー。  
  
 Get アクセサー`SlowerDP`までの値を返す前に 3 秒間待機、`_slowerDP`データ メンバー。  
  
 Get アクセサー`SlowestDP`までの値を返す前に 5 秒間待機、`_slowestDP`データ メンバー。  
  
> [!NOTE]
>  この例は、デモンストレーション目的のみで提供されます。 [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]桁違いのフィールド セットをよりも、プロパティ定義のガイドラインをお勧めします。 詳細については、次を参照してください。[を選択するプロパティとメソッド](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100))します。  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A>プロパティが上記にバインド`AsyncDS`を使用して<xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 バインディング エンジンが処理するときに、<xref:System.Windows.Data.Binding>オブジェクトの場合、最初の開始<xref:System.Windows.Data.Binding>がバインドされている、`SlowestDP`プロパティ。 ときにこの<xref:System.Windows.Data.Binding>は、処理は返されません値が正常にためがスリープ状態を 5 秒間、そのため、[次へ]<xref:System.Windows.Data.Binding>要素が処理されます。 次<xref:System.Windows.Data.Binding>は正常に完了しなかった値が 3 秒間スリープ状態にあるためです。 バインディング エンジンは、次に、移動<xref:System.Windows.Data.Binding>にバインドする要素を`FastDP`プロパティ。 これは、 <xref:System.Windows.Data.Binding> "高速 Value"の値を返します。 <xref:System.Windows.Controls.TextBlock> "高速 Value"の値が表示されます。  
  
 3 秒が経過した後、 `SlowerDP` "低速 Value"の値を返します。 <xref:System.Windows.Controls.TextBlock> "低速 Value"の値が表示されます。  
  
 5 秒が経過した後、 `SlowestDP` 「最も低速な値」の値を返します。 そのバインディングは、最初に表示されているために、最高の優先順位が。 <xref:System.Windows.Controls.TextBlock>に「最も低速な値」の値が表示されます。  
  
 参照してください<xref:System.Windows.Data.PriorityBinding>については、バインドからの成功した戻り値と見なされます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

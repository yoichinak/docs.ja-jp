---
title: '方法: PriorityBinding を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 4be1ce434eb1e169e8a19b56c92ca1efb48773d2
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169081"
---
# <a name="how-to-implement-prioritybinding"></a>方法: PriorityBinding を実装する
<xref:System.Windows.Data.PriorityBinding>で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、バインドのリストを指定します。 バインドの一覧は、優先順位が最も高い順に並べ替えられます。 最も優先順位の高いバインドが処理時に値を正常に返す場合、リスト内の他のバインドを処理する必要はありません。 最も優先度の高いバインドが評価されるまでに長い時間がかかる場合もありますが、高い優先順位のバインドによって値が正常に返されるまで、値が正常に返される次に高い優先順位が使用されます。  
  
## <a name="example"></a>例  
 がどのよう<xref:System.Windows.Data.PriorityBinding>に機能`AsyncDataSource`するかを示すために、オブジェクトは`FastDP`、 `SlowerDP`、、および`SlowestDP`の3つのプロパティを使用して作成されています。  
  
 の`FastDP` get アクセサーは、 `_fastDP`データメンバーの値を返します。  
  
 の`SlowerDP` get アクセサーは、 `_slowerDP`データメンバーの値を返す前に3秒間待機します。  
  
 の`SlowestDP` get アクセサーは、5秒間待機してから、 `_slowestDP`データメンバーの値を返します。  
  
> [!NOTE]
> この例は、デモンストレーション目的のみで提供されます。 .NET ガイドラインでは、フィールドセットよりも速度が低いプロパティを定義することをお勧めします。 詳細については、「[プロパティとメソッドの選択](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100))」を参照してください。  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 プロパティ<xref:System.Windows.Controls.TextBlock.Text%2A>は、を使用し`AsyncDS`て<xref:System.Windows.Data.PriorityBinding>上記のにバインドされます。  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 バインディングエンジンは、 <xref:System.Windows.Data.Binding>オブジェクトを処理するときに、 `SlowestDP`プロパティに<xref:System.Windows.Data.Binding>バインドされている最初のから開始します。 この<xref:System.Windows.Data.Binding>処理が完了すると、5秒間スリープ状態になるため、値は正常に返されませ<xref:System.Windows.Data.Binding>ん。そのため、次の要素が処理されます。 次<xref:System.Windows.Data.Binding>のは、3秒間スリープ状態になるため、値を正常に返しません。 バインドエンジンは、 <xref:System.Windows.Data.Binding> `FastDP`プロパティにバインドされている次の要素に移動します。 これ<xref:System.Windows.Data.Binding>により、"Fast value" という値が返されます。 で<xref:System.Windows.Controls.TextBlock>値 "Fast value" が表示されるようになりました。  
  
 3秒が経過すると`SlowerDP` 、プロパティは値 "低速値" を返します。 次<xref:System.Windows.Controls.TextBlock>に、値 "低速値" が表示されます。  
  
 5秒が経過すると`SlowestDP` 、プロパティは "低速値" という値を返します。 最初にリストされているので、そのバインディングの優先順位は最も高くなります。 で<xref:System.Windows.Controls.TextBlock>は、"低速値" という値が表示されるようになりました。  
  
 バインディング<xref:System.Windows.Data.PriorityBinding>から成功した戻り値と見なされる内容については、「」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

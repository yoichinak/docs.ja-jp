---
title: '方法: バインドされた項目の一覧に基づいて値を生成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: c2ec5ff26c89649294df266e790445e5aa5d08ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200520"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>方法: バインドされた項目の一覧に基づいて値を生成する
<xref:System.Windows.Data.MultiBinding> ソースのプロパティの一覧にバインディング ターゲット プロパティをバインドし、特定の入力で値を生成するためのロジックを適用できます。 この例を使用して、<xref:System.Windows.Data.MultiBinding>します。  
  
## <a name="example"></a>例  
 次の例では、`NameListData` は、`PersonName` オブジェクトのコレクションを参照します。このオブジェクトは、`firstName` と `lastName` の 2 つのプロパティを含みます。 次の例で、<xref:System.Windows.Controls.TextBlock>最後の名前を持つ人物の姓と名の最初を示します。  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 姓が先の形式を生成する方法を理解するには、次に示す `NameConverter` の実装をご覧ください。  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` 実装、<xref:System.Windows.Data.IMultiValueConverter>インターフェイス。 `NameConverter` 個々 のバインディングから値を取得し、値オブジェクトの配列に格納します。 順序、<xref:System.Windows.Data.Binding>要素は、下に表示されます、<xref:System.Windows.Data.MultiBinding>要素は、これらの値が配列に格納されている順序。 値、<xref:System.Windows.Data.MultiBinding.ConverterParameter%2A>のパラメーターの引数によって参照される属性、<xref:System.Windows.Data.MultiBinding.Converter%2A>メソッドで、名前を書式設定する方法を決定するパラメーターの切り替えを実行します。  
  
## <a name="see-also"></a>関連項目

- [バインドされたデータを変換する](how-to-convert-bound-data.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法のトピック](data-binding-how-to-topics.md)

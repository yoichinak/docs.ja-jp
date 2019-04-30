---
title: '方法: バインドされたデータを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 40699bec1c6cd775f7f8495b7a49eda15fb2ed83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020934"
---
# <a name="how-to-convert-bound-data"></a>方法: バインドされたデータを変換する
この例では、バインドで使用されるデータへの変換を適用する方法を示します。  
  
 バインド中にデータを変換するには、実装するクラスを作成する必要があります、<xref:System.Windows.Data.IValueConverter>が含まれているインターフェイス、<xref:System.Windows.Data.IValueConverter.Convert%2A>と<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>メソッド。  
  
## <a name="example"></a>例  
 次の例では、年、月、および日のみが表示されるように渡される日付値に変換する日付コンバーターの実装を示します。 実装する場合、<xref:System.Windows.Data.IValueConverter>装飾を使用して実装することをお勧めは、インターフェイス、<xref:System.Windows.Data.ValueConversionAttribute>開発を指定する属性を次の例のように、変換に関連するデータ型のツールします。  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 コンバーターを作成した後にリソースとして追加できます、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。 次の例では、 *src*を名前空間にマップ*DateConverter*が定義されています。  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最後に、次の構文を使用して、バインディングでコンバーターを使用できます。 次の例では、テキストの内容、<xref:System.Windows.Controls.TextBlock>にバインドされた*StartDate*、外部データ ソースのプロパティであります。  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 上記の例で参照されるスタイルのリソースは、このトピックで示されていませんリソース セクションで定義されます。  
  
## <a name="see-also"></a>関連項目

- [バインディングの検証の実装](how-to-implement-binding-validation.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

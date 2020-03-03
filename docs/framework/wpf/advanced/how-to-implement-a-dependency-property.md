---
title: '方法: 依存関係プロパティを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400355"
---
# <a name="how-to-implement-a-dependency-property"></a>方法: 依存関係プロパティを実装する
この例では、共通言語ランタイム (CLR) プロパティを<xref:System.Windows.DependencyProperty>フィールドで戻して、依存関係プロパティを定義する方法を示します。 独自に定義したプロパティが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまな機能、たとえばスタイル、データ バインディング、継承、アニメーション、既定値をサポートできるようにするには、そのプロパティを依存関係プロパティとして実装します。  
  
## <a name="example"></a>例  
 次の例では、最初に<xref:System.Windows.DependencyProperty.Register%2A>メソッドを呼び出して依存関係プロパティを登録します。 依存関係プロパティの名前と特性を格納するために使用する識別子フィールドの名前は、 <xref:System.Windows.DependencyProperty.Name%2A> <xref:System.Windows.DependencyProperty.Register%2A>呼び出しの一部として、依存関係プロパティに対して選択したで、リテラル`Property`文字列によって追加される必要があります。 たとえば、 <xref:System.Windows.DependencyProperty.Name%2A>の`Location`を使用して依存関係プロパティを登録する場合、依存関係プロパティに定義する識別子フィールドの名前`LocationProperty`はにする必要があります。  
  
 この例で`State`は、依存関係プロパティとその CLR アクセサーの名前はです。識別子フィールドは`StateProperty`です。プロパティの型は<xref:System.Boolean>で、依存関係プロパティ`MyStateControl`を登録する型はです。  
  
 このパターンに従って名前が付けられていない場合は、定義したプロパティがデザイナーから正しく報告されず、プロパティ システムのスタイル適用の一部が予期したとおりに動作しなくなる可能性があります。  
  
 依存関係プロパティの既定のメタデータを指定することもできます。 `State` 依存関係プロパティの既定値を `false` として登録する例を次に示します。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 プライベートフィールドで CLR プロパティをバックアップするだけではなく、依存関係プロパティを実装する方法と理由の詳細については、「[依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [依存関係プロパティの概要](dependency-properties-overview.md)
- [方法トピック](properties-how-to-topics.md)

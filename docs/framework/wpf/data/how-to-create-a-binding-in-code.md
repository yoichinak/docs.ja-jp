---
title: '方法: コードでバインディングを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 666dbb4e2de0e8a7a83d6e0dfda50822cfdfd860
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371187"
---
# <a name="how-to-create-a-binding-in-code"></a>方法: コードでバインディングを作成する
この例は、コード中で<xref:System.Windows.Data.Binding>を作成し設定する方法を示します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.FrameworkElement>クラスと<xref:System.Windows.FrameworkContentElement>クラスは、`SetBinding`メソッドを公開しています。 これらのクラスを継承する要素をバインドする場合、<xref:System.Windows.FrameworkElement.SetBinding%2A>メソッドを直接呼び出すことができます。  
  
 次の例は、`MyDataProperty`という名前のプロパティを持つ`MyData`という名前のクラスを作成しています。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 次の例では、バインディング オブジェクトを作成し、ソースを設定する方法を示します。  この例では、<xref:System.Windows.Controls.TextBlock>コントロールである`myText`の<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティを、`MyDataProperty`にバインドするために<xref:System.Windows.FrameworkElement.SetBinding%2A>を用いています。  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 完全なコード サンプルでは、[コードのみのバインドのサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))を参照してください。  
  
 <xref:System.Windows.FrameworkElement.SetBinding%2A>を呼び出す代わりに、<xref:System.Windows.Data.BindingOperations>クラスの静的メソッド<xref:System.Windows.Data.BindingOperations.SetBinding%2A>を使用することができます。 次の例では、<xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>の代わりに<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>メソッドを呼び出して、`myText`を`myDataProperty`にバインドしています。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>関連項目
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

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
この例を作成し、設定する方法を示しています、<xref:System.Windows.Data.Binding>コード。

## <a name="example"></a>例
 <xref:System.Windows.FrameworkElement>クラスおよび<xref:System.Windows.FrameworkContentElement>クラスの両方を公開、`SetBinding`メソッド。 これらのクラスを継承する要素をバインドする場合を呼び出すことができます、<xref:System.Windows.FrameworkElement.SetBinding%2A>メソッドを直接します。

 次の例は、という名前のクラスを作成`MyData`、という名前のプロパティを含む`MyDataProperty`します。

 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]

 次の例では、バインディング、バインディングのソースを設定するオブジェクトを作成する方法を示します。  この例では<xref:System.Windows.FrameworkElement.SetBinding%2A>にバインドする、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティの`myText`、これは、<xref:System.Windows.Controls.TextBlock>コントロールに`MyDataProperty`。

 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]

 完全なコード サンプルでは、次を参照してください。[コードのみのバインドのサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))します。

 呼び出す代わりに<xref:System.Windows.FrameworkElement.SetBinding%2A>、使用することができます、<xref:System.Windows.Data.BindingOperations.SetBinding%2A>の静的メソッド、<xref:System.Windows.Data.BindingOperations>クラス。 次の例で呼び出し<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>の代わりに<xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>にバインドする`myText`に`myDataProperty`します。

 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]

## <a name="see-also"></a>関連項目
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

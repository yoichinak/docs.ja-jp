---
title: '方法: Windows フォーム コントロールをファクトリ オブジェクトにバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: b64545528746e50d00f88d626a07ac98839e926c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589736"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>方法: Windows フォーム コントロールをファクトリ オブジェクトにバインドする
データをやり取りするコントロールを作成している際に、他のオブジェクトを生成するオブジェクトやメソッドにコントロールをバインドすることが必要な場合があります。 このようなオブジェクトやメソッドは、ファクトリと呼ばれます。 たとえば、データ ソースがメモリまたは型内のオブジェクトではなく、メソッドの呼び出しからの戻り値の場合があります。 ソースがコレクションを返す限り、コントロールをこの種類のデータ ソースにバインドできます。  
  
 <xref:System.Windows.Forms.BindingSource> コントロールを使用して、コントロールをファクトリ オブジェクトに簡単にバインドすることができます。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Forms.BindingSource> コントロールを使用して、<xref:System.Windows.Forms.DataGridView> コントロールをファクトリ メソッドにバインドする方法を示します。 ファクトリ メソッドの名前は `GetOrdersByCustomerId` であり、Northwind データベースで、特定の顧客のすべての注文を返します。  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource コンポーネント](bindingsource-component.md)
- [方法: Windows フォーム コントロールを型にバインドします。](how-to-bind-a-windows-forms-control-to-a-type.md)

---
title: '方法: BindingSource ResetItem メソッドを使用して変更通知を発生させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 68073f245e1a2eb18a277d7011ca0183dabb3724
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085065"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>方法: BindingSource ResetItem メソッドを使用して変更通知を発生させる
コントロールのデータ ソースの中には、項目が変更、追加、または削除されても変更通知が発生しないものがあります。 <xref:System.Windows.Forms.BindingSource> コンポーネントを使用すると、そのようなデータ ソースをバインドし、コードから変更通知を発生させることができます。  
  
## <a name="example"></a>例  
 このフォームは、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用してリストを <xref:System.Windows.Forms.DataGridView> コントロールにバインドする方法を示しています。 リストは変更通知を発生しないため、リスト内の項目が変更されると、<xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.ResetItem%2A> メソッドが呼び出されます。 .  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 Visual Basic または Visual C# のコマンドラインからこの例をビルドする方法については、[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 この例は、新しいプロジェクトにコードを貼り付けることによって Visual Studio で構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource コンポーネント](bindingsource-component.md)
- [方法: Windows フォーム コントロールを型にバインドします。](how-to-bind-a-windows-forms-control-to-a-type.md)

---
title: '方法: オブジェクトを Windows フォーム DataGridView コントロールにバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 02c4f94eddfcf782d7d2323787d9b6a9b18db2d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180259"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>方法: オブジェクトを Windows フォーム DataGridView コントロールにバインドする
各オブジェクトが別々の行として表示されるように <xref:System.Windows.Forms.DataGridView> コントロールにオブジェクトのコレクションをバインドする方法を次のコード例に示します。 また、この例では、<xref:System.Windows.Forms.DataGridViewComboBoxColumn> にプロパティとして列挙型を表示し、コンボ ボックスのドロップダウン リストに列挙値が含まれるようにする方法も示されています。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
 この例をコマンドラインから Visual Basic または Visual C# にビルドする方法の詳細については、[コマンドラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView 行にバインドされたオブジェクトへのアクセス](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)

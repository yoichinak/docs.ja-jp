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
ms.openlocfilehash: e1fef71de799f9f906c956a0441c92e027173a1c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612342"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>方法: オブジェクトを Windows フォーム DataGridView コントロールにバインドする
各オブジェクトが別々の行として表示されるように <xref:System.Windows.Forms.DataGridView> コントロールにオブジェクトのコレクションをバインドする方法を次のコード例に示します。 また、この例では、<xref:System.Windows.Forms.DataGridViewComboBoxColumn> にプロパティとして列挙型を表示し、コンボ ボックスのドロップダウン リストに列挙値が含まれるようにする方法も示されています。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView 行にバインドされたオブジェクトへのアクセス](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)

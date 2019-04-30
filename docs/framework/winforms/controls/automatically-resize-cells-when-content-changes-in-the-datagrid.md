---
title: '方法: Windows フォームの DataGridView コントロールの内容変更時にセルのサイズを自動的に変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: 7acd7777ede726b9dfed2b821e4248a0ebf7797f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954324"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>方法: Windows フォームの DataGridView コントロールの内容変更時にセルのサイズを自動的に変更する
コンテンツが変更されたときは常に行、列、ヘッダーのサイズを自動的に変更し、クリッピングなしでセルが値を表示するのに十分な大きさになるように、 <xref:System.Windows.Forms.DataGridView> コントロールを構成できます。  
  
 新しいサイズを決定するために使用するセルを制限する多くのオプションがあります。 たとえば、現在表示されている行の値のみに基づいて、その列の幅のサイズを自動的に変更するコントロールを構成できます。 これにより、大量の行を処理するときの非効率性を回避できますが、この場合では、 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> などのサイズ調整のメソッドを使用して、選択時にサイズを調整することをお勧めします。  
  
 自動サイズ変更の詳細については、「 [Windows フォーム DataGridView コントロールのサイズ変更オプション](sizing-options-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 次のコード例は、自動サイズ変更に使用できるオプションを示します。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
- Visual Basic または Visual C# からこの例をビルドする方法については、[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)、または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Windows フォーム DataGridView コントロール内の列と行のサイズ変更](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールのサイズ変更オプション](sizing-options-in-the-windows-forms-datagridview-control.md)
- [方法: プログラムで Windows フォームの DataGridView コントロールのコンテンツに合わせてセルのサイズを変更します。](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)

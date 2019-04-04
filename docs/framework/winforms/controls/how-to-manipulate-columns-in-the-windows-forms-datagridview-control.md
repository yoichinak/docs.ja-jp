---
title: '方法: Windows フォームの DataGridView コントロール内の列を操作します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGridView control [Windows Forms], manipulating columns
- columns [Windows Forms], manipulating
- data grids [Windows Forms], manipulating columns
ms.assetid: d8cfe6b3-bbab-4182-bec2-0517d9f1eaf6
ms.openlocfilehash: 95d41093178c56c999ecfe515a380927513e715d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722452"
---
# <a name="how-to-manipulate-columns-in-the-windows-forms-datagridview-control"></a>方法: Windows フォームの DataGridView コントロール内の列を操作します。

<xref:System.Windows.Forms.DataGridViewColumn> クラスのプロパティを使用して <xref:System.Windows.Forms.DataGridView> の列を操作するさまざまな方法を次のコード例に示します。

## <a name="example"></a>例

[!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewColumnDemo.cpp#100)]
[!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewColumnDemo.cs#100)]
[!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewcolumndemo.vb#100)]

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。

コマンドラインからこの例を Visual Basic または Visual c# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング](programming-with-cells-rows-and-columns-in-the-datagrid.md)

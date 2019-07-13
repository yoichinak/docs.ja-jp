---
title: '方法: Windows フォーム ListView コントロールに挿入マークを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: f3dff351052eaaf70737c6410c1367ab568f6fd0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586520"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>方法: Windows フォーム ListView コントロールに挿入マークを表示する
<xref:System.Windows.Forms.ListView> コントロールの挿入マークは、ドラッグされた項目の挿入先となるポイントをユーザーに表示します。 ユーザーが項目をその他の 2 つの項目の間のポイントにドラッグすると、項目の予期される新しい場所に挿入マークが表示されます。  
  
> [!NOTE]
>  挿入マーク機能は、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> メソッドを呼び出した場合に、[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] でのみ使用できます。 以前のオペレーティング システムでは、挿入マークに関連するすべてのコードは効果がなく、挿入マークは表示されません。 詳細については、「 <xref:System.Windows.Forms.ListViewInsertionMark> 」を参照してください。  
  
 次の図は、挿入マークを示しています。  
  
 ![ListView の挿入マークを示すスクリーン ショット。](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")  
  
 この機能の使用方法を次のコード例に示します。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [ListView コントロール](listview-control-windows-forms.md)
- [ListView コントロールの概要](listview-control-overview-windows-forms.md)
- [チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)

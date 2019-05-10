---
title: '方法: Windows フォーム ListView コントロール内の項目を選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 41a30ba6c242d0587e98b458e41ca213e8885bca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638200"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>方法: Windows フォーム ListView コントロール内の項目を選択する
この例では、Windows Forms <xref:System.Windows.Forms.ListView> コントロールで項目をプログラムで選択する方法を示します。 プログラムで項目を選択しても、<xref:System.Windows.Forms.ListView> コントロールへのフォーカスは自動的には変更されません。 このため、通常は項目を設定するときにその項目をフォーカスもするように設定できます。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- A<xref:System.Windows.Forms.ListView>という名前のコントロール`listView1`を少なくとも 1 つの項目を格納しています。  
  
- <xref:System?displayProperty=nameWithType> 名前空間と <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間への参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>

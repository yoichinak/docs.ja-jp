---
title: '方法: Windows フォーム DataGridView コントロールの新しい行に既定値を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 8a90cbef7032fd3753a6c9ec0b856a4e2ea1db27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193695"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールの新しい行に既定値を指定する
行うことができますデータ エントリより便利なアプリケーションがいっぱいになる既定の新しく追加された行の値。 <xref:System.Windows.Forms.DataGridView>クラスを入力できる既定の値を<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>イベント。 ユーザーが新しいレコードの行を入力すると、このイベントが発生します。 コードでは、このイベントを処理する場合は、任意のセルに独自の値を設定できます。  
  
 次のコード例を使用して新しい行の既定値を指定する方法を示します、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>イベント。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   A`NewCustomerId`を一意に生成する関数`CustomerID`値。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールにおける新規レコード行の使用](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)

---
title: '方法: Windows フォームの DataGridView コントロールの編集モードを指定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 00c5bb85eb1b238371e58a631d90b69a41c49140
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725307"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>方法: Windows フォームの DataGridView コントロールの編集モードを指定します。
既定では、ユーザーが現在の内容を編集できる<xref:System.Windows.Forms.DataGridView>テキスト ボックスのセルに入力するか、F2 キーを押します。 これにより、セル編集モードでのすべての次の条件が満たされた場合。  
  
-   基になるデータ ソースは、編集をサポートします。  
  
-   <xref:System.Windows.Forms.DataGridView>制御を有効にします。  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A>プロパティの値が<xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>します。  
  
-   `ReadOnly`セル、行、列、およびコントロールのプロパティは、すべてのセットを`false`します。  
  
 編集モードで、ユーザーはセルの値を変更して、元の値にセルを元に戻すには、esc キー、変更をコミットするには ENTER キーを押します。  
  
 構成することができます、<xref:System.Windows.Forms.DataGridView>制御が現在のセルとセルが編集モードに入るようにします。 」と入力し、ESC キーの動作は変更されていないこの場合が、値がコミットまたは元に戻す、セルが編集モードでは残ります。 セルまたは f2 キーを押すときにのみユーザーが入力されたときにのみ、セルが編集モードを入力できるように、コントロールを構成することもできます。 最後に、セルを防ぐため除くを呼び出すと編集モードに入ることができます、<xref:System.Windows.Forms.DataGridView.BeginEdit%2A>メソッド。  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>DataGridView コントロールの編集モードを変更するには  
  
-   設定、<xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>プロパティを適切な<xref:System.Windows.Forms.DataGridViewEditMode>列挙体。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   
  <xref:System> アセンブリおよび <xref:System.Windows.Forms> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)

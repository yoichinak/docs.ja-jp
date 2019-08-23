---
title: '方法: Windows フォームの NumericUpDown コントロールの書式を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949162"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>方法: Windows フォームの NumericUpDown コントロールの書式を設定する
Windows フォーム<xref:System.Windows.Forms.NumericUpDown>コントロールでの値の表示方法を構成できます。 プロパティ<xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>は、小数点の後に表示される数字の数を決定します。既定値は0です。 プロパティ<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>は、3桁の10進数の間に区切り記号を挿入するかどう`false`かを決定します。既定値はです。 <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>プロパティがに`true`設定されている場合、コントロールは、10進形式ではなく16進数で`false`値を表示できます。既定値はです。  
  
### <a name="to-format-the-numeric-value"></a>数値の書式を設定するには  
  
- <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>プロパティを整数に設定し、 <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>プロパティをまたは`false`に`true`設定して、10進値を表示します。  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     \- または -  
  
- <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>プロパティをに`true`設定して、16進数の値を表示します。  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    > 値が16進数としてフォームに表示されている場合でも、 <xref:System.Windows.Forms.NumericUpDown.Value%2A>プロパティに対して実行するすべてのテストでは、その10進値がテストされます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown コントロール](numericupdown-control-windows-forms.md)
- [NumericUpDown コントロールの概要](numericupdown-control-overview-windows-forms.md)

---
title: '方法: プログラムで Windows フォーム DomainUpDown コントロールに項目を追加します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 06c2c83ddfba67aaff775065cc2aa4515978bf81
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722712"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>方法: プログラムで Windows フォーム DomainUpDown コントロールに項目を追加します。
Windows フォームに項目を追加する<xref:System.Windows.Forms.DomainUpDown>コード内でコントロールできます。 呼び出す、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>または<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>のメソッド、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>をコントロールの項目を追加するクラス<xref:System.Windows.Forms.DomainUpDown.Items%2A>プロパティ。 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>メソッドは、コレクションの末尾に項目を追加中に、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>メソッドは、指定した位置にある項目を追加します。  
  
### <a name="to-add-a-new-item"></a>新しい項目を追加するには  
  
1.  使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>項目のリストの末尾に項目を追加する方法。  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     - または -  
  
2.  使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>指定位置にあるリストに項目を挿入するメソッド。  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [DomainUpDown コントロール](domainupdown-control-windows-forms.md)
- [DomainUpDown コントロールの概要](domainupdown-control-overview-windows-forms.md)

---
title: '方法: Windows フォームの DomainUpDown コントロールから項目を削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: 0c07365f5be2e419b4049a466949fed2d884d897
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131405"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>方法: Windows フォームの DomainUpDown コントロールから項目を削除する
項目を削除するには、Windows フォームから<xref:System.Windows.Forms.DomainUpDown>コントロールを呼び出すことによって、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>または<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>のメソッド、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>クラス。 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>メソッドは、特定のアイテムを削除中に、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>メソッドは、位置を使用して項目を削除します。  
  
### <a name="to-remove-an-item"></a>アイテムを削除するには  
  
-   使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>のメソッド、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>名前で項目を削除するクラス。  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     - または -  
  
-   使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>位置を使用して項目を削除するメソッド。  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [DomainUpDown コントロール](domainupdown-control-windows-forms.md)
- [DomainUpDown コントロールの概要](domainupdown-control-overview-windows-forms.md)

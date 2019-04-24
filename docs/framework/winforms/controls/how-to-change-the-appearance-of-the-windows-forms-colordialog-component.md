---
title: '方法: Windows フォーム ColorDialog コンポーネントの表示形式を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: d2bb9e06d9d84a9b61c67510e9c012066f69d55e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329233"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>方法: Windows フォーム ColorDialog コンポーネントの表示形式を変更する
Windows フォームの外観を構成する<xref:System.Windows.Forms.ColorDialog>コンポーネント プロパティの数にします。 ダイアログ ボックスが 2 つのセクションでは、いずれかの基本色とカスタムの色を定義するユーザーを許可する 1 つを示しています。  
  
 ほとんどのプロパティは、ユーザーがダイアログ ボックスから選択できる色を制限します。 場合、<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>プロパティに設定されて`true`、カスタムの色を定義するユーザーを許可します。 <xref:System.Windows.Forms.ColorDialog.FullOpen%2A>プロパティは`true`; カスタムの色を定義する ダイアログ ボックスが展開されている場合はそれ以外の場合、ユーザーが「カスタム色の定義」ボタンする必要がありますクリックします。 ときに、<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>プロパティに設定されて`true`、ダイアログ ボックスは、基本色のセットで使用可能なすべての色を表示します。 場合、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>プロパティに設定されて`true`ユーザーがディザリングされた色を選択できません; を選択する純色のみ利用できます。  
  
 場合、<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>プロパティに設定されて`true`、ダイアログ ボックスで、[ヘルプ] ボタンが表示されます。 ユーザーがヘルプ ボタンをクリックすると、<xref:System.Windows.Forms.ColorDialog>コンポーネントの<xref:System.Windows.Forms.CommonDialog.HelpRequest>イベントが発生します。  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>色のダイアログ ボックスの外観を構成するには  
  
1. 設定、 <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>、 <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>、 <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>、および<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>プロパティを目的の値にします。  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog コンポーネント](colordialog-component-windows-forms.md)
- [ColorDialog コンポーネントの概要](colordialog-component-overview-windows-forms.md)

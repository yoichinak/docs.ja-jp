---
title: ColorDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 7dd48c8df0a36262962df596e8efadf4de1c2cd3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713333"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog コンポーネントの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ColorDialog>コンポーネントは、ユーザー、パレットから色を選択して、そのパレットにカスタムの色を追加できる構成済みのダイアログ ボックス。 このダイアログ ボックスは、他の Windows ベースのアプリケーションで表示される色を選択するためのダイアログ ボックスと同じです。 このコントロールは、独自のダイアログ ボックスを使用しない簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。  
  
 ダイアログ ボックスで選択した色が返されます、<xref:System.Windows.Forms.ColorDialog.Color%2A>プロパティ。 場合、<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>プロパティに設定されて`false`、「カスタムの色を定義する」ボタンが無効になり、ユーザーは、パレットで定義済みの色に制限されます。 場合、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>プロパティに設定されて`true`ユーザーがディザリングされた色を選択できません。 ダイアログ ボックスを表示するには、呼び出す必要があるその<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog コンポーネント](colordialog-component-windows-forms.md)
- [ダイアログ ボックス コントロールおよびコンポーネント](dialog-box-controls-and-components-windows-forms.md)
- [方法: Windows フォーム ColorDialog コンポーネントの外観を変更します。](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)

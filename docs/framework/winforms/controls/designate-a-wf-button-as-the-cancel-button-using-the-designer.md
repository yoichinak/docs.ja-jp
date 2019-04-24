---
title: '方法: デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: f127a1a74643c975aea73b24896c098b365aa327
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327543"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>方法: デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する
任意の Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールをキャンセル ボタン。 ユーザーがフォーム上の他のコントロールにフォーカスがあるか、ESC キーを押すと [キャンセル] ボタンをクリックします。 このようなボタンは通常、ユーザーは、すばやく操作をコミットせずに操作を終了できるようにする設定します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-designate-the-cancel-button"></a>[キャンセル] ボタンを指定するには  
  
1. ボタンが存在するフォームを選択します。  
  
2. **プロパティ**ウィンドウで、設定フォームの<xref:System.Windows.Forms.Form.CancelButton%2A>プロパティを<xref:System.Windows.Forms.Button>コントロールの名前。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button コントロールの概要](button-control-overview-windows-forms.md)
- [Windows フォームの Button コントロールを選択する方法](ways-to-select-a-windows-forms-button-control.md)
- [方法: Windows フォームのボタン クリックに応答するには](how-to-respond-to-windows-forms-button-clicks.md)
- [方法: Windows フォームの Button をデザイナーの使用を承認ボタンとして指定します。](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button コントロール](button-control-windows-forms.md)

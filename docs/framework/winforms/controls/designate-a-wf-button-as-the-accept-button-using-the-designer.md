---
title: '方法: Windows フォームの Button をデザイナーの使用を承認ボタンとして指定します。'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 61f0c99560d008cc10c94403ac936e5b97267d3a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707652"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>方法: Windows フォームの Button をデザイナーの使用を承認ボタンとして指定します。
任意の Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを承認ボタン、既定のボタンとも呼ばれます。 ユーザーが ENTER キーを押すと、フォームの他のコントロールにフォーカスがあるの既定のボタンがクリックされました。 フォーカスを持つコントロールが別のボタン例外:、フォーカスのあるボタンをクリックする場合、-複数行テキスト ボックス、または ENTER キーをトラップするカスタム コントロール。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-designate-the-accept-button"></a>同意する ボタンを指定するには  
  
1.  ボタンが存在するフォームを選択します。  
  
2.  **プロパティ**ウィンドウで、設定フォームの<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを<xref:System.Windows.Forms.Button>コントロールの名前。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button コントロールの概要](button-control-overview-windows-forms.md)
- [Windows フォームの Button コントロールを選択する方法](ways-to-select-a-windows-forms-button-control.md)
- [方法: Windows フォームのボタン クリックに応答するには](how-to-respond-to-windows-forms-button-clicks.md)
- [方法: デザイナーを使用して、[キャンセル] ボタンとして Windows フォームの Button を指定します。](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button コントロール](button-control-windows-forms.md)

---
title: RadioButton コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: 1210658226d9bcacbf4904fdc90a9908c34f5b73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129117"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.RadioButton>コントロールがユーザーに一連の 2 つ以上の相互に排他的な選択肢を提示します。 同様に機能するラジオ ボタンおよびチェック ボックスがあります、中には、重要な違いがあります。 ユーザーは、ラジオ ボタンを選択するときに、同じグループ内の他のオプション ボタンをも選択できません。 これに対し、任意の数のチェック ボックスを選択できます。 ユーザーに通知するラジオ ボタン グループを定義する、"Here is の選択肢の 1 つだけを選択できます"  
  
## <a name="using-the-control"></a>コントロールを使用します。  
 ときに、<xref:System.Windows.Forms.RadioButton>コントロールをクリックすると、その<xref:System.Windows.Forms.RadioButton.Checked%2A>プロパティに設定されて`true`と<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが呼び出されます。 <xref:System.Windows.Forms.RadioButton.CheckedChanged>イベントが発生したときの値、<xref:System.Windows.Forms.RadioButton.Checked%2A>プロパティの変更。 場合、<xref:System.Windows.Forms.RadioButton.AutoCheck%2A>プロパティに設定されて`true`(既定) ラジオ ボタンを選択すると、グループの他のすべては自動的にクリアします。 このプロパティは通常にしか設定`false`ラジオ ボタンが選択されていることを確認する検証コードを使用する場合は、有効なオプションです。 コントロール内で表示されるテキストに設定されて、<xref:System.Windows.Forms.Control.Text%2A>プロパティで、アクセス キーのショートカットを含めることができます。 アクセス キーには、アクセス キーと ALT キーを押して、コントロールを「クリックして」にユーザーができます。 詳細については、「[方法 :Windows フォーム コントロールのアクセス キーを作成](how-to-create-access-keys-for-windows-forms-controls.md)と[方法。によって表示されるテキストを設定、Windows フォーム コントロール](how-to-set-the-text-displayed-by-a-windows-forms-control.md)します。  
  
 <xref:System.Windows.Forms.RadioButton>場合に選択した場合、押されたように見えますコマンド ボタンのように、コントロールの表示、<xref:System.Windows.Forms.RadioButton.Appearance%2A>プロパティに設定されて<xref:System.Windows.Forms.Appearance.Button>します。 ラジオ ボタンを使用してイメージを表示も、<xref:System.Windows.Forms.ButtonBase.Image%2A>と<xref:System.Windows.Forms.ButtonBase.ImageList%2A>プロパティ。 詳細については、「[方法 :によって表示されるイメージの設定を Windows フォーム コントロール](how-to-set-the-image-displayed-by-a-windows-forms-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.RadioButton>
- [Panel コントロールの概要 (Windows フォーム)](panel-control-overview-windows-forms.md)
- [GroupBox コントロールの概要 (Windows フォーム)](groupbox-control-overview-windows-forms.md)
- [CheckBox コントロールの概要 (Windows フォーム)](checkbox-control-overview-windows-forms.md)
- [方法: Windows フォーム コントロールのアクセス キーを作成する](how-to-create-access-keys-for-windows-forms-controls.md)
- [方法: Windows フォーム コントロールによって表示されるテキストを設定する](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [方法: セットとして機能する Windows フォーム RadioButton コントロールをグループ化する](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton コントロール](radiobutton-control-windows-forms.md)

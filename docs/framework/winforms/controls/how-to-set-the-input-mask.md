---
title: '方法: 定型入力を設定する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06eaf68fef167d63e6f8404dd5049f5445881d24
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331469"
---
# <a name="how-to-set-the-input-mask"></a>方法: 定型入力を設定する
マスクされたテキスト ボックス コントロールは、許可または拒否のユーザー入力の宣言の構文をサポートする強化されたテキスト ボックス コントロールです。 Mask プロパティを設定して、アプリケーションで任意のカスタム検証ロジックを記述することがなく、使用可能なユーザー入力を指定できます。 詳細については、の「解説」を参照してください、<xref:System.Windows.Forms.MaskedTextBox>クラス。  
  
## <a name="setting-the-mask-property-manually"></a>Mask プロパティを手動で設定  
 Mask プロパティをサポートする文字に精通する場合は、手動で入力することができます。 Mask プロパティをサポートする、文字の概要については、「解説」を参照してください、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティ。  
  
#### <a name="to-set-the-mask-property-manually"></a>Mask プロパティを手動で設定するには  
  
1. **デザイン**ビューで、<xref:System.Windows.Forms.MaskedTextBox>します。  
  
2. **プロパティ**ウィンドウで、検索、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティ。  
  
3. 使用するマスクを入力します。 たとえば、「 `###`」と入力します。  
  
## <a name="using-the-input-mask-dialog-box"></a>[定型入力] ダイアログ ボックスを使用します。  
 [定型入力] ダイアログ ボックスでは、いくつか定義済みの入力マスクを提供します。 定義済みのマスクを変更または、独自のマスクを手動で入力することもできます。  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>定型入力 ダイアログ ボックスを開きます  
  
1. **デザイン**ビューで、<xref:System.Windows.Forms.MaskedTextBox>します。  
  
    1.  [スマート タグを開く] をクリックして、 **MaskedTextBox タスク**パネル。  
  
    2.  クリックして**マスクを設定する**します。  
  
     \- または -  
  
    1.  **プロパティ**ウィンドウで、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティ。  
  
    2.  プロパティの値列の省略記号ボタンをクリックします。  
  
     **定型入力** ダイアログ ボックスが表示されます。  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>定型入力 ダイアログ ボックスを使用するには  
  
1. (省略可能)一覧で定義済みのマスクのいずれかをクリックします。  
  
2. (省略可能)定義済みのマスクを編集、**マスク**ボックス。  
  
3. (省略可能)新しいマスクを入力、**マスク**ボックス。 定義済みのマスクのいずれかを使用する必要はありません。  
  
    > [!NOTE]
    >  [プレビュー] ボックスでユーザーに表示される文字の表示、<xref:System.Windows.Forms.MaskedTextBox>します。 これらの文字は、データを正しく入力するユーザーを支援するガイドです。  
  
4. オンまたはオフ、**使用 ValidatingType**チェック ボックスをオンします。 **使用 ValidatingType**  チェック ボックスは、ユーザーがデータ入力を検証するデータ型を使用するかどうかを指定します。 詳細については、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> プロパティを参照してください。  
  
5. **[OK]** をクリックします。  
  
     マスクを入力、**マスク**プロパティ、**プロパティ**ウィンドウ。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: MaskedTextBox コントロールの使用](walkthrough-working-with-the-maskedtextbox-control.md)

---
title: '方法: 定型入力を設定する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949143"
---
# <a name="how-to-set-the-input-mask"></a>方法: 定型入力を設定する
マスクされたテキストボックスコントロールは、ユーザー入力を受け入れたり拒否したりするための宣言構文をサポートする、強化されたテキストボックスコントロールです。 Mask プロパティを設定することによって、アプリケーションにカスタム検証ロジックを記述することなく、許容されるユーザー入力を指定できます。 詳細については、 <xref:System.Windows.Forms.MaskedTextBox>クラスの「解説」を参照してください。  
  
## <a name="setting-the-mask-property-manually"></a>Mask プロパティを手動で設定する  
 Mask プロパティでサポートされている文字に慣れている場合は、手動で入力できます。 Mask プロパティでサポートされる文字の概要については、 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティの「解説」を参照してください。  
  
### <a name="to-set-the-mask-property-manually"></a>Mask プロパティを手動で設定するには  
  
1. **デザイン**ビューで、を選択<xref:System.Windows.Forms.MaskedTextBox>します。  
  
2. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティを見つけます。  
  
3. 目的のマスクを入力します。 たとえば、「 `###`」と入力します。  
  
## <a name="using-the-input-mask-dialog-box"></a>[定型入力] ダイアログボックスの使用  
 [定型入力] ダイアログボックスには、定義済みの入力マスクがいくつか用意されています。 また、定義済みのマスクを変更したり、独自のマスクを手動で入力したりすることもできます。  
  
### <a name="to-open-the-input-mask-dialog-box"></a>[定型入力] ダイアログボックスを開くには  
  
1. **デザイン**ビューで、を選択<xref:System.Windows.Forms.MaskedTextBox>します。  
  
    1. スマートタグをクリックして、 **[MaskedTextBox タスク]** パネルを開きます。  
  
    2. **[マスクの設定]** をクリックします。  
  
     \- または -  
  
    1. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティを選択します。  
  
    2. [プロパティ値] 列の省略記号ボタンをクリックします。  
  
     **[定型入力]** ダイアログボックスが表示されます。  
  
### <a name="to-use-the-input-mask-dialog-box"></a>[定型入力] ダイアログボックスを使用するには  
  
1. Optional一覧で、定義済みマスクのいずれかをクリックします。  
  
2. Optional **[マスク]** ボックスで、定義済みのマスクを編集します。  
  
3. Optional **[マスク]** ボックスに新しいマスクを入力します。 つまり、定義済みのマスクのいずれかを使用する必要はありません。  
  
    > [!NOTE]
    > [プレビュー] ボックスに、ユーザーがに<xref:System.Windows.Forms.MaskedTextBox>表示する文字が表示されます。 これらの文字は、ユーザーがデータを正しく入力するのに役立つガイドです。  
  
4. **[ValidatingType を使用する]** チェックボックスをオンまたはオフにします。 [ **ValidatingType を使用**する] チェックボックスは、ユーザーによるデータ入力の検証にデータ型を使用するかどうかを指定します。 詳細については、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> プロパティを参照してください。  
  
5. **[OK]** をクリックします。  
  
     マスクは、 **[プロパティ]** ウィンドウの**mask**プロパティに入力します。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: MaskedTextBox コントロールの操作](walkthrough-working-with-the-maskedtextbox-control.md)

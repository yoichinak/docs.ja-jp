---
title: '方法: Windows フォームの Label コントロールでアクセス キーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: ffe4bf6fb29e82b04938e2ba9a2d9d21e5eabcde
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314309"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>方法: Windows フォームの Label コントロールでアクセス キーを作成する
Windows フォーム<xref:System.Windows.Forms.Label>他のコントロールのアクセス キーを定義するコントロールを使用できます。 ラベル コントロールにアクセス キーを定義するときに、ユーザーは、ALT キーとそれに続くタブ オーダー内でコントロールにフォーカスを移動する指定した文字に押すことができます。 ラベルは、フォーカスを受け取ることはできません、ために、タブ オーダー内で次のコントロールに自動的にフォーカスが移動します。 この手法を使用して、テキスト ボックス、コンボ ボックス、リスト ボックス、およびデータ グリッドをアクセス キーを割り当てます。  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>ラベルを持つコントロールに、アクセス キーを割り当てるには  
  
1. 最初に、ラベルを描画し、その他のコントロールを描きます。  
  
     - または -  
  
     任意の順序で、コントロールを描画し、設定、<xref:System.Windows.Forms.Control.TabIndex%2A>を他のコントロールより 1 少ない数のラベルのプロパティ。  
  
2. ラベルの設定<xref:System.Windows.Forms.Label.UseMnemonic%2A>プロパティを`true`します。  
  
3. アンパサンド (&) は、ラベルの<xref:System.Windows.Forms.Label.Text%2A>ラベルのアクセス キーを割り当てるプロパティを。 詳細については、次を参照してください。 [Windows のフォーム コントロールのアクセス キーを作成する](how-to-create-access-keys-for-windows-forms-controls.md)します。  
  
    > [!NOTE]
    >  アクセス キーの作成に使用するのではなく、ラベル コントロールにアンパサンドを表示することがあります。 これは、アンパサンドがデータに含まれるレコード セット内のフィールドにラベル コントロールをバインドする場合に発生する可能性があります。 ラベル コントロールでは、アンパサンドを表示するには、設定、<xref:System.Windows.Forms.Label.UseMnemonic%2A>プロパティを`false`します。 アンパサンドを表示しても、アクセス キーがある場合は、設定、<xref:System.Windows.Forms.Label.UseMnemonic%2A>プロパティを`true`とアクセス キーは 1 つのアンパサンド (&)、アンパサンドを 2 つのアンパサンドを表示します。  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a>関連項目

- [方法: Windows フォーム Label コントロールのサイズを内容に合わせて変更する](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Label コントロールの概要](label-control-overview-windows-forms.md)
- [Label コントロール](label-control-windows-forms.md)

---
title: '方法: Windows フォーム コントロールのアクセス キーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: e6c829553163359301bad2cd896fc43562ee8069
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334459"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>方法: Windows フォーム コントロールのアクセス キーを作成する
*アクセス キー*がメニューやメニュー項目では、ボタンなどのコントロールのラベルのテキストに下線付きの文字。 アクセス キーでは、ユーザーことができます「ボタンをクリック」を組み合わせて定義済みのアクセス キーを持つ、ALT キーを押してします。 たとえば、フォームを印刷する手順を実行するボタンとその`Text`プロパティが「印刷」に設定されて、文字"P"により、文字"P"を実行時に、ボタンのテキストに下線が引かあります前にアンパサンドを追加します。 ユーザーには、ALT キーを押しながら P キーを押して、ボタンに関連付けられているコマンドを実行できます。 フォーカスを受け取ることはできませんが、コントロールのアクセス キーを持つことはできません。  
  
### <a name="to-create-an-access-key-for-a-control"></a>コントロールのアクセス キーを作成するには  
  
1. 設定、`Text`プロパティ ショートカットとなる文字の前にアンパサンドを含む文字列 (&)。  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  アクセス キーを作成することがなく、キャプションにアンパサンドを含める、2 つのアンパサンドを含める (& &)。 単一のアンパサンドがキャプションに表示され、文字に下線を付けるありません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Button>
- [方法: Windows フォームのボタン クリックに応答するには](how-to-respond-to-windows-forms-button-clicks.md)
- [方法: によって表示されるテキストを設定、Windows フォーム コントロール](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)

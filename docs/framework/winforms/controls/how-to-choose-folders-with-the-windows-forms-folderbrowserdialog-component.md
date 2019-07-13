---
title: '方法: Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: 050af6d10faec3dd09998349dcf96e96ea0f9201
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746926"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>方法: Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する
多くの場合、作成した Windows アプリケーション内で、フォルダーを選択するようにユーザーに促す必要があります。とりわけ、一連のファイルを保存するように求める場合が多いです。 Windows フォーム<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントでは、このタスクを簡単に実行できます。  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog コンポーネントを使用してフォルダーを選択するには  
  
1. プロシージャでは、確認、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントの<xref:System.Windows.Forms.Form.DialogResult%2A> ダイアログ ボックスが閉じられた方法を表示しの値を取得するプロパティ、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントの<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>プロパティ。  
  
2. ダイアログ ボックスのツリー ビュー内に表示されるフォルダーを最上位を設定する必要がある場合は、設定、<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>のメンバーを受け取りますプロパティ、<xref:System.Environment.SpecialFolder>列挙体。  
  
3. さらに、設定、<xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>フォルダー ブラウザーのツリー ビューの上部にある文字列をテキストを指定するには、プロパティが表示されます。  
  
     次の例で、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントを使用して Visual Studio でプロジェクトを作成し、保存するフォルダーを選択するように求められますのようなフォルダーを選択します。 この例で、フォルダー名に表示されますが、<xref:System.Windows.Forms.TextBox>フォーム上のコントロール。 編集可能な領域になど場所を配置することをお勧め、<xref:System.Windows.Forms.TextBox>制御、ユーザーがエラーまたはその他の問題が発生した場合、選択項目を編集可能性があります。 この例では使用して、フォーム、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントと<xref:System.Windows.Forms.TextBox>コントロール。  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  このクラスを使用するアセンブリに必要です特権レベルを付与して、<xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>一部であるプロパティの<xref:System.Security.Permissions.FileIOPermissionAccess>列挙体。 部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないため例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](../../misc/code-access-security-basics.md)」をご覧ください。  
  
 ファイルを保存する方法については、次を参照してください。[方法。SaveFileDialog コンポーネントを使用してファイルを保存](how-to-save-files-using-the-savefiledialog-component.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog コンポーネントの概要 (Windows フォーム)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog コンポーネント](folderbrowserdialog-component-windows-forms.md)

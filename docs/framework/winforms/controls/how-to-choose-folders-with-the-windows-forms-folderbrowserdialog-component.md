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
ms.openlocfilehash: fc19ea466f535f783d3b0537a973ce41c223902d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046131"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>方法: Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する

多くの場合、作成した Windows アプリケーション内で、フォルダーを選択するようにユーザーに促す必要があります。とりわけ、一連のファイルを保存するように求める場合が多いです。 Windows フォーム<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントを使用すると、このタスクを簡単に実行できます。

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog コンポーネントを使用してフォルダーを選択するには

1. プロシージャで、 <xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントの<xref:System.Windows.Forms.Form.DialogResult%2A>プロパティを調べて、ダイアログボックスがどのように閉じられたかを確認<xref:System.Windows.Forms.FolderBrowserDialog>し、 <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>コンポーネントのプロパティの値を取得します。

2. ダイアログボックスのツリービュー内に表示される最上位のフォルダーを設定する必要がある場合は、 <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> <xref:System.Environment.SpecialFolder>列挙体のメンバーを取得するプロパティを設定します。

3. また、 <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>プロパティを設定することもできます。このプロパティは、フォルダーブラウザーのツリービューの上部に表示されるテキスト文字列を指定します。

    次の例では、 <xref:System.Windows.Forms.FolderBrowserDialog> Visual Studio でプロジェクトを作成する場合と同様に、コンポーネントを使用してフォルダーを選択し、保存先のフォルダーを選択するように求められます。 この例では、フォルダー名がフォーム上の<xref:System.Windows.Forms.TextBox>コントロールに表示されます。 エラーやその他の問題が発生した場合にユーザーが選択内容を<xref:System.Windows.Forms.TextBox>編集できるように、コントロールなどの編集可能な領域に場所を配置することをお勧めします。 この例では、 <xref:System.Windows.Forms.FolderBrowserDialog>コンポーネント<xref:System.Windows.Forms.TextBox>とコントロールを含むフォームが想定されています。

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
    > このクラスを使用するには、アセンブリに、 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> <xref:System.Security.Permissions.FileIOPermissionAccess>列挙体の一部であるプロパティによって付与される特権レベルが必要です。 部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないため例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](../../misc/code-access-security-basics.md)」をご覧ください。

ファイルを保存する方法の詳細につい[ては、「」を参照してください。SaveFileDialog コンポーネント](how-to-save-files-using-the-savefiledialog-component.md)を使用してファイルを保存します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog コンポーネントの概要 (Windows フォーム)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog コンポーネント](folderbrowserdialog-component-windows-forms.md)

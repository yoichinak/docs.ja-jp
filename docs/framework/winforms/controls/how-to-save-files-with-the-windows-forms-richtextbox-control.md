---
title: '方法: Windows フォームの RichTextBox コントロールを使用してファイルを保存する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: 4784ddd563ccec0f7e6271700781ee1b5d3ac105
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318417"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>方法: Windows フォームの RichTextBox コントロールを使用してファイルを保存する
Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールがいくつかの形式のいずれかで表示される情報を書き込むことができます。  
  
-   プレーンテキスト  
  
-   Unicode のプレーン テキスト  
  
-   リッチ テキスト形 (式 RTF)  
  
-   OLE オブジェクトの代わりにスペースを含む RTF  
  
-   プレーン テキストの OLE オブジェクトのテキスト表現を使用  
  
 ファイルを保存する、<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>メソッド。 使用することも、 **SaveFile**をストリームにデータを保存するメソッド。 詳細については、「 <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29> 」を参照してください。  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>コントロールの内容をファイルに保存するには  
  
1. 保存するファイルのパスを決定します。  
  
     実際のアプリケーションでは、通常使用する、<xref:System.Windows.Forms.SaveFileDialog>コンポーネント。 概要については、次を参照してください。 [SaveFileDialog コンポーネントの概要](savefiledialog-component-overview-windows-forms.md)します。  
  
2. 呼び出す、<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>のメソッド、<xref:System.Windows.Forms.RichTextBox>コントロール、ファイルを保存して、必要に応じてファイルの種類を指定します。 唯一の引数としてファイル名を持つメソッドを呼び出す場合、ファイルは RTF として保存されます。 別の種類のファイルを指定するには、2 番目の引数として <xref:System.Windows.Forms.RichTextBoxStreamType> 列挙型の値を指定します。  
  
     リッチ テキスト ファイルの場所は次の例で、パスが設定、 **My Documents**フォルダー。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターにはでこのフォルダーが含まれていると想定できるために使用されます。 この場所を選択すると、ユーザーは最小限のシステム アクセスのレベルでアプリケーションを安全に実行もできます。 次の例でフォームを前提としています、<xref:System.Windows.Forms.RichTextBox>コントロールが既に追加されています。  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。 アプリケーション ファイルを作成する場合は、そのアプリケーションの フォルダーの作成アクセス必要があります。 アクセス許可は、アクセス制御リストを使って設定します。 ファイルが既に存在する場合、アプリケーションには、書き込みアクセスだけより低い権限が必要があります。 可能であれば、デプロイ時に、ファイルを作成し、のみ 1 つのファイルに対する読み取りアクセス権を付与ではなくフォルダーの作成アクセスする方が安全です。 また、ルート フォルダーや Program Files フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox コントロール](richtextbox-control-windows-forms.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)

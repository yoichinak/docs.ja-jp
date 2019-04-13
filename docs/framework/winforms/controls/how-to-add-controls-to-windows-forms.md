---
title: '方法: Windows フォームにコントロールを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 04597283a8ff2e21a0f227268671d3605eac6356
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343590"
---
# <a name="how-to-add-controls-to-windows-forms"></a>方法: Windows フォームにコントロールを追加する
ほとんどのフォームは、ユーザー インターフェイス (UI) を定義するフォームのサーフェイスにコントロールを追加して設計されています。 A*コントロール*は情報を表示するか、ユーザー入力をそのまま使用するためのフォーム上のコンポーネントです。 コントロールの詳細については、次を参照してください。 [Windows フォーム コントロール](index.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-draw-a-control-on-a-form"></a>フォームのコントロールを描画するには  
  
1. フォームを開きます。 詳細については、「[方法 :デザイナーで Windows フォームを表示](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))します。  
  
2. **ツールボックス**フォームに追加するコントロールをクリックします。  
  
3. フォーム、検索するコントロールの左上隅をクリックし、検索するコントロールの右下隅を先にドラッグします。  
  
     コントロールは、指定した位置とサイズをフォームに追加されます。  
  
    > [!NOTE]
    >  各コントロールには、定義されている既定のサイズがあります。 コントロールの既定のサイズで、フォームにコントロールを追加するにはからドラッグすることで、**ツールボックス**をフォームにします。  
  
### <a name="to-drag-a-control-to-a-form"></a>コントロールをフォームにドラッグするには  
  
1. フォームを開きます。 詳細については、「[方法 :デザイナーで Windows フォームを表示](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))します。  
  
2. **ツールボックス**フォームにドラッグしてコントロールをクリックします。  
  
     コントロールは、既定のサイズで指定した場所にあるフォームに追加されます。  
  
    > [!NOTE]
    >  コントロールをダブルクリックすることができます、**ツールボックス**既定のサイズで、フォームの左上隅に追加します。  
  
     実行時に、フォームにコントロールを動的に追加することができますも。 次のコード例で、<xref:System.Windows.Forms.TextBox>コントロールがフォームに追加時に、<xref:System.Windows.Forms.Button>コントロールがクリックされました。  
  
    > [!NOTE]
    >  次の手順が使用して、フォームが存在する必要があります、**ボタン**コントロール、`Button1`に既に配置した、します。  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>プログラムでコントロールをフォームに追加するには  
  
1. ボタンを処理するメソッドで`Click`、制御変数への参照を追加するには、次のようなコードを挿入、フォームのクラス内のイベントの設定、コントロールの`Location`コントロールを追加します。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  コントロールの他のプロパティを初期化するコードを追加することもできます。  
  
    > [!IMPORTANT]
    >  悪意のあるを参照して、ローカル コンピューターがネットワーク経由のセキュリティ リスクを公開する`UserControl`します。 誤ってそれをプロジェクトに追加した後に、有害なカスタム コントロールを作成する悪意のあるユーザーの場合の問題のみなります。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [方法: Windows フォーム上のコントロールのサイズを変更する](how-to-resize-controls-on-windows-forms.md)
- [方法: Windows フォーム コントロールによって表示されるテキストを設定する](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)

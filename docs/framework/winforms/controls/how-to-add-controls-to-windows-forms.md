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
ms.openlocfilehash: 5c57d86b2f08733dc4a729bf6091eab23c6035f2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039707"
---
# <a name="how-to-add-controls-to-windows-forms"></a>方法: Windows フォームにコントロールを追加する
ほとんどのフォームは、ユーザーインターフェイス (UI) を定義するためにフォームの画面にコントロールを追加することによって設計されています。 *コントロール*は、情報の表示やユーザー入力の受け入れに使用されるフォーム上のコンポーネントです。 コントロールの詳細については、「 [Windows フォームコントロール](index.md)」を参照してください。

## <a name="to-draw-a-control-on-a-form"></a>フォームにコントロールを描画するには

1. フォームを開きます。 詳細については、「[方法 :デザイナー](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))で Windows フォームを表示します。

2. **ツールボックス**で、フォームに追加するコントロールをクリックします。

3. フォームで、コントロールの左上隅を配置する場所をクリックして、コントロールの右下隅を配置する場所にドラッグして、をドラッグします。

     コントロールが、指定された位置とサイズでフォームに追加されます。

    > [!NOTE]
    >  各コントロールには、既定のサイズが定義されています。 コントロールを**ツールボックス**からフォームにドラッグすると、コントロールの既定のサイズでコントロールをフォームに追加できます。

## <a name="to-drag-a-control-to-a-form"></a>コントロールをフォームにドラッグするには

1. フォームを開きます。 詳細については、「[方法 :デザイナー](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))で Windows フォームを表示します。

2. **ツールボックス**で、目的のコントロールをクリックし、フォームにドラッグします。

     コントロールは、既定のサイズで指定された位置にフォームに追加されます。

    > [!NOTE]
    >  **ツールボックス**のコントロールをダブルクリックすると、既定のサイズでフォームの左上隅に追加できます。

     また、実行時にコントロールをフォームに動的に追加することもできます。 次のコード例<xref:System.Windows.Forms.TextBox>では、コントロールがクリックさ<xref:System.Windows.Forms.Button>れると、コントロールがフォームに追加されます。

    > [!NOTE]
    >  次の手順では、**ボタン**コントロール`Button1`が既に配置されているフォームが存在する必要があります。

## <a name="to-add-a-control-to-a-form-programmatically"></a>プログラムによってフォームにコントロールを追加するには

1. フォームのクラス内のボタンの`Click`イベントを処理するメソッドで、次のようなコードを挿入して、コントロール変数への参照を追加し、コントロールの`Location`を設定して、コントロールを追加します。

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
    >  また、コントロールの他のプロパティを初期化するコードを追加することもできます。

    > [!IMPORTANT]
    >  悪意`UserControl`のあるを参照することにより、ネットワーク経由でローカルコンピューターをセキュリティ上のリスクにさらすことがあります。 これは、悪意のあるユーザーが有害なカスタムコントロールを作成した後、誤ってプロジェクトに追加した場合にのみ問題になります。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [方法: Windows フォームのコントロールのサイズを変更する](how-to-resize-controls-on-windows-forms.md)
- [方法: Windows フォームコントロールによって表示されるテキストを設定する](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)

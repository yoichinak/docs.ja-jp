---
title: 'チュートリアル: ドラッグ アンド ドロップ操作を実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182444"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行
Windows ベースのアプリケーション内でドラッグ アンド ドロップ操作を実行するには、一連のイベント 、特に<xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragLeave>、、、、、および<xref:System.Windows.Forms.Control.DragDrop>イベントを処理する必要があります。 これらのイベントのイベント引数で使用できる情報を操作することで、ドラッグ アンド ドロップ操作を簡単に行うことができます。  
  
## <a name="dragging-data"></a>データのドラッグ  
 ドラッグ アンド ドロップ操作はすべてドラッグから始まります。 ドラッグの開始時にデータを収集できるようにする機能が<xref:System.Windows.Forms.Control.DoDragDrop%2A>メソッドに実装されています。  
  
 次の例では、<xref:System.Windows.Forms.Control.MouseDown>最も直感的な操作であるため、このイベントを使用してドラッグ操作を開始しています (ドラッグ アンド ドロップ操作の大部分は、マウス ボタンが押し込まれている状態で始まります)。 ただし、ドラッグ アンド ドロップ プロシージャを開始するために、どのイベントも使用できることに注意してください。  
  
> [!NOTE]
> 特定のコントロールには、カスタムドラッグ固有のイベントがあります。 コントロール<xref:System.Windows.Forms.ListView>と<xref:System.Windows.Forms.TreeView>コントロールには、たとえば、イベント<xref:System.Windows.Forms.TreeView.ItemDrag>があります。  
  
#### <a name="to-start-a-drag-operation"></a>ドラッグ操作を開始するには  
  
1. ドラッグを<xref:System.Windows.Forms.Control.MouseDown>開始するコントロールのイベントでは、`DoDragDrop`ドラッグするデータを設定するメソッドを使用し、ドラッグできる効果をドラッグできます。 詳細については、「 <xref:System.Windows.Forms.DragEventArgs.Data%2A> および <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>」を参照してください。  
  
     次の例は、ドラッグ操作を開始する方法を示しています。 ドラッグを開始するコントロールは<xref:System.Windows.Forms.Button>コントロール、ドラッグされるデータは<xref:System.Windows.Forms.Control.Text%2A><xref:System.Windows.Forms.Button>コントロールのプロパティを表す文字列、許可された効果はコピーまたは移動のいずれかになります。  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > メソッドでは、任意の`DoDragDrop`データをパラメーターとして使用できます。上の例では、<xref:System.Windows.Forms.Control.Text%2A><xref:System.Windows.Forms.Button>コントロールのプロパティが (値をハードコーディングしたり、データセットからデータを取得したりするのではなく) 使用しました。 <xref:System.Windows.Forms.Button> Windows ベースのアプリケーションにドラッグ アンド ドロップ操作を組み込む際には、この点に留意してください。  
  
 ドラッグ操作が有効な場合、ドラッグ操作を<xref:System.Windows.Forms.Control.QueryContinueDrag>続行するためにシステムの「許可を要求する」イベントを処理できます。 このメソッドを処理する場合は、ドラッグ操作<xref:System.Windows.Forms.TreeNode><xref:System.Windows.Forms.TreeView>に影響を与えるメソッドを呼び出すのも適切なポイントです。  
  
## <a name="dropping-data"></a>データの削除  
 Windows フォームまたはコントロール上の場所からデータをドラッグし始めたら、自然な場所にドロップします。 データをドロップするように正しく構成されているフォームまたはコントロールの領域を横切ると、カーソルは変化します。 Windows フォームまたはコントロール内の任意の領域は、プロパティを設定し<xref:System.Windows.Forms.Control.AllowDrop%2A><xref:System.Windows.Forms.Control.DragEnter>、および<xref:System.Windows.Forms.Control.DragDrop>イベントを処理することによって、ドロップされたデータを受け入れることができます。  
  
#### <a name="to-perform-a-drop"></a>ドロップを実行するには  
  
1. プロパティを<xref:System.Windows.Forms.Control.AllowDrop%2A>true に設定します。  
  
2. ドロップが`DragEnter`発生するコントロールのイベントで、ドラッグされるデータが許容可能な型 (この場合は<xref:System.Windows.Forms.Control.Text%2A>) であることを確認します。 次に、ドロップが発生したときに発生する影響を列挙型の値に設定します<xref:System.Windows.Forms.DragDropEffects>。 詳細については、<xref:System.Windows.Forms.DragEventArgs.Effect%2A> を参照してください。  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > 独自の<xref:System.Windows.Forms.DataFormats>オブジェクトをメソッドのパラメータとして指定することで、独自の<xref:System.Object>オブジェクトを<xref:System.Windows.Forms.DataObject.SetData%2A>定義できます。 これを行う際には、指定されたオブジェクトがシリアル化可能であることを確認してください。 詳細については、<xref:System.Runtime.Serialization.ISerializable> を参照してください。  
  
3. ドロップが<xref:System.Windows.Forms.Control.DragDrop>発生するコントロールのイベントでは、メソッドを<xref:System.Windows.Forms.DataObject.GetData%2A>使用して、ドラッグするデータを取得します。 詳細については、<xref:System.Security.Cryptography.Xml.DataObject.Data%2A> を参照してください。  
  
     次の例では、<xref:System.Windows.Forms.TextBox>コントロールはドラッグ先のコントロールです (ドロップが発生します)。 このコードは、<xref:System.Windows.Forms.Control.Text%2A>ドラッグするデータ<xref:System.Windows.Forms.TextBox>と同じコントロールのプロパティを設定します。  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > また、<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>ドラッグ アンド ドロップ操作中に押されたキーによっては、特定の効果が発生するようにプロパティを操作することもできます (たとえば、Ctrl キーを押したときにドラッグされたデータをコピーするのが標準です)。  
  
## <a name="see-also"></a>関連項目

- [方法 : クリップボードにデータを追加する](how-to-add-data-to-the-clipboard.md)
- [方法 : クリップボードからデータを取得する](how-to-retrieve-data-from-the-clipboard.md)
- [ドラッグ アンド ドロップ操作とクリップボードのサポート](drag-and-drop-operations-and-clipboard-support.md)

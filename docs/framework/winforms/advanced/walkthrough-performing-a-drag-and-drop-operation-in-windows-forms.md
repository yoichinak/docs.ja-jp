---
title: 'チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: f7551f28d07c9517865f60af99954eb40e57daa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747395"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行
Windows ベースのアプリケーション内でドラッグ アンド ドロップ操作を実行する必要がありますを処理する、一連のイベント、特に、 <xref:System.Windows.Forms.Control.DragEnter>、 <xref:System.Windows.Forms.Control.DragLeave>、および<xref:System.Windows.Forms.Control.DragDrop>イベント。 利用可能な情報、イベントのこれらのイベントの引数を使用して、ドラッグ アンド ドロップ操作を簡単に実行できます。  
  
## <a name="dragging-data"></a>データのドラッグ  
 すべてのドラッグ アンド ドロップ操作は、ドラッグから始まります。 ドラッグの開始時に収集されるようにデータを有効にする機能は実装、<xref:System.Windows.Forms.Control.DoDragDrop%2A>メソッド。  
  
 次の例では、<xref:System.Windows.Forms.Control.MouseDown>最も直感的なために、ドラッグ操作を開始するイベントを使用 (ほとんどのドラッグ アンド ドロップ操作は、マウス ボタンが押されているで始まります)。 ただし、ドラッグ アンド ドロップ手順を開始するすべてのイベントを使用できることに注意してください。  
  
> [!NOTE]
>  特定のコントロールでは、カスタム ドラッグ固有のイベントがあります。 <xref:System.Windows.Forms.ListView>と<xref:System.Windows.Forms.TreeView>コントロール、たとえば、ある、<xref:System.Windows.Forms.TreeView.ItemDrag>イベント。  
  
#### <a name="to-start-a-drag-operation"></a>ドラッグ操作を開始するには  
  
1. <xref:System.Windows.Forms.Control.MouseDown> 、ドラッグを開始する場所を使用してコントロールのイベントを`DoDragDrop`ドラッグされるデータを設定するメソッドと許可される効果をドラッグすることになります。 詳細については、次のトピックを参照してください。 <xref:System.Windows.Forms.DragEventArgs.Data%2A> および <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>  
  
     次の例では、ドラッグ操作を開始する方法を示します。 コントロールのドラッグが開始されるは、<xref:System.Windows.Forms.Button>コントロール、ドラッグされているデータは、文字列を表す、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、<xref:System.Windows.Forms.Button>制御、および許可された効果は、コピーまたは移動します。  
  
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
    >  すべてのデータをパラメーターとして使用できます、`DoDragDrop`メソッドは、上記の例で、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、 <xref:System.Windows.Forms.Button> (ではなく、値をハードコーディングまたはデータセットからデータを取得する) 制御が使用されたプロパティに関連していたため、ドラッグされている場所 (、<xref:System.Windows.Forms.Button>コントロール)。 ドラッグ アンド ドロップ操作を Windows ベースのアプリケーションに組み込む場合に、この点に留意してください。  
  
 ドラッグ操作が有効な状態を処理できます、 <xref:System.Windows.Forms.Control.QueryContinueDrag> 「アクセス許可を要求する」、イベントのドラッグ操作を続行するシステム。 このメソッドを処理するときにも、適切なポイントを展開するなど、ドラッグ操作に影響があるメソッドを呼び出すことの<xref:System.Windows.Forms.TreeNode>で、<xref:System.Windows.Forms.TreeView>上にカーソルを合わせると制御します。  
  
## <a name="dropping-data"></a>データを削除します。  
 データの場所から Windows フォームまたはコントロールのドラッグを開始した後どこかにドロップするが自然です。 フォームまたはデータを削除するが正しく構成されているコントロールの領域を超えたときに、カーソルは変更されます。 Windows フォームまたはコントロール内で任意の領域を設定して、ドロップしたデータを受け入れるようにできる、<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティと処理、<xref:System.Windows.Forms.Control.DragEnter>と<xref:System.Windows.Forms.Control.DragDrop>イベント。  
  
#### <a name="to-perform-a-drop"></a>ドロップを実行するには  
  
1. 設定、<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティを true にします。  
  
2. `DragEnter`ドラッグされているデータが適切な型が、ドロップが行われるコントロールのイベントを確認します (この場合、 <xref:System.Windows.Forms.Control.Text%2A>)。 コードの値に、ドロップが発生したときに行われる効果を設定し、<xref:System.Windows.Forms.DragDropEffects>列挙体。 詳細については、「 <xref:System.Windows.Forms.DragEventArgs.Effect%2A> 」を参照してください。  
  
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
    >  独自に定義することができます<xref:System.Windows.Forms.DataFormats>オブジェクトとして指定することによって、<xref:System.Object>のパラメーター、<xref:System.Windows.Forms.DataObject.SetData%2A>メソッド。 確認、これについては、指定されたオブジェクトがシリアル化可能なことです。 詳細については、「 <xref:System.Runtime.Serialization.ISerializable> 」を参照してください。  
  
3. <xref:System.Windows.Forms.Control.DragDrop>使用して、ドロップが行われるコントロールのイベントを<xref:System.Windows.Forms.DataObject.GetData%2A>ドラッグされているデータを取得します。 詳細については、「 <xref:System.Security.Cryptography.Xml.DataObject.Data%2A> 」を参照してください。  
  
     次の例で、<xref:System.Windows.Forms.TextBox>コントロールは、(ドロップが行われる) にドラッグされているコントロール。 コードのセット、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>制御ドラッグされているデータに相当します。  
  
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
    >  さらに、使用できる、<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>プロパティ、キーによって、ドラッグ アンド ドロップ操作中に押されているように、特定の効果の発生 (たとえばには、CTRL キーが押されたときに、ドラッグしたデータをコピーする標準的な)。  
  
## <a name="see-also"></a>関連項目

- [方法: データをクリップボードに追加します。](how-to-add-data-to-the-clipboard.md)
- [方法: クリップボードからデータを取得します。](how-to-retrieve-data-from-the-clipboard.md)
- [ドラッグ アンド ドロップ操作とクリップボードのサポート](drag-and-drop-operations-and-clipboard-support.md)

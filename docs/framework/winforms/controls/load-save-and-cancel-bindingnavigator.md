---
title: '方法: Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991736"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>方法: Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する

コントロールは、データにバインドさ<xref:System.Windows.Forms.ToolStrip>れているフォーム上のコントロールを移動および操作するための特殊な用途のコントロールです。 <xref:System.Windows.Forms.BindingNavigator>

コントロールであるため、コンポーネントを簡単に変更して、ユーザーの追加または別のコマンドを含めることができます。<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.BindingNavigator>

次の手順<xref:System.Windows.Forms.TextBox>では、コントロールがデータ<xref:System.Windows.Forms.ToolStrip>にバインドされ、フォームに追加されたコントロールが、[読み込み]、[保存]、および [キャンセル] の各ボタンを含むように変更されます。

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>[Load]、[save]、[cancel] の各ボタンを BindingNavigator コンポーネントに追加します。

1. Visual Studio で、フォームに<xref:System.Windows.Forms.TextBox>コントロールを追加します。

2. データソースにバインド<xref:System.Windows.Forms.BindingSource>されているにバインドします。 この例<xref:System.Windows.Forms.BindingSource>では、がデータベースにバインドされています。

3. データセットとテーブルアダプターが生成されたら、 <xref:System.Windows.Forms.BindingNavigator>コントロールをフォームにドラッグします。

4. コントロールの<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>プロパティを、 <xref:System.Windows.Forms.BindingSource>コントロールにバインドされているフォーム上のに設定します。 <xref:System.Windows.Forms.BindingNavigator>

5. <xref:System.Windows.Forms.BindingNavigator> コントロールを選択します。

6. **[BindingNavigator タスク]** ダイアログボックスが表示されるように、スマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) をクリックし、 **[アイテムの編集]** を選択します。

     **項目コレクションエディター**が表示されます。

7. **Items コレクションエディター**で、次の手順を実行します。

    1. 適切な<xref:System.Windows.Forms.ToolStripSeparator>種類の<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripItem>を選択し、 **[追加]** ボタンをクリックして、3つの項目を追加します。

    2. ボタンのプロパティを loadbutton、savebutton、および cancelbutton にそれぞれ設定します。 <xref:System.Windows.Forms.ToolStripItem.Name%2A>

    3. 読み込み、**保存**、 **キャンセル**の各ボタンのプロパティを設定します。<xref:System.Windows.Forms.ToolStripItem.Text%2A>

    4. 各ボタン<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>のプロパティを **[テキスト]** に設定します。 または、このプロパティを**image**または**imageandtext**に設定し、 <xref:System.Windows.Forms.ToolStripItem.Image%2A>プロパティに表示されるようにイメージを設定することもできます。

    5. **[OK]** をクリックしてダイアログ ボックスを閉じます。 ボタンがに<xref:System.Windows.Forms.ToolStrip>追加されます。

8. フォームを右クリックし、 **[コードの表示]** を選択します。

9. コードエディターで、テーブルアダプターにデータを読み込むコード行を見つけます。 このコードは、手順 2. でデータバインディングを設定したときに生成されました。 コードは次`TableAdapterName.Fill(DataSetName.TableName)`のようになります。 通常、フォームの<xref:System.Windows.Forms.Form.Load>イベントに含まれます。

10. 前に作成した<xref:System.Windows.Forms.ToolStripItem.Click> **読み込み** <xref:System.Windows.Forms.ToolStripButton>のイベントのイベントハンドラーを作成し、このデータ読み込みコードをそのイベントに移動します。

     これで、コードは次のようになります。

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. 前の手順で作成し<xref:System.Windows.Forms.ToolStripItem.Click>た**保存**<xref:System.Windows.Forms.ToolStripButton>のイベントのイベントハンドラーを作成し、コントロールがバインドされているテーブル内のデータを更新するコードを記述します。

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > 場合<xref:System.Windows.Forms.BindingNavigator>によっては、コンポーネントに **[保存]** ボタンが既に存在していても、Windows フォームデザイナーによってコードが生成されていないことがあります。 この場合は、 <xref:System.Windows.Forms.ToolStripItem.Click> <xref:System.Windows.Forms.ToolStrip>上にまったく新しいボタンを作成するのではなく、そのボタンのイベントハンドラーに上記のコードを配置できます。 ただし、ボタンは既定で無効になっているので、 <xref:System.Windows.Forms.ToolBarButton.Enabled%2A>ボタンのプロパティをに`true`設定して、ボタンが正しく機能するようにする必要があります。

12. 前に作成した<xref:System.Windows.Forms.ToolStripItem.Click> **キャンセル** <xref:System.Windows.Forms.ToolStripButton>のイベントのイベントハンドラーを作成し、表示されるデータレコードに対する変更を取り消すコードを記述します。

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > メソッド<xref:System.Windows.Forms.BindingSource.CancelEdit%2A>のスコープは、データの行です。 次のレコードに移動する前に、個々のレコードを表示しているときに行ったすべての変更を保存します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
- [BindingSource コンポーネントの概要](bindingsource-component-overview.md)

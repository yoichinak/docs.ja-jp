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
ms.openlocfilehash: f190bfa29af480fa104f30b21b1af517c413b838
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211577"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>方法: Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する

<xref:System.Windows.Forms.BindingNavigator>コントロールが特別な用途<xref:System.Windows.Forms.ToolStrip>移動し、フォーム上のデータにバインドされているコントロールを操作することが想定されているコントロール。

ある、<xref:System.Windows.Forms.ToolStrip>コントロール、<xref:System.Windows.Forms.BindingNavigator>コンポーネントは、ユーザーの追加のまたは別のコマンドを含めるに簡単に変更できます。

次の手順で、<xref:System.Windows.Forms.TextBox>コントロールがデータにバインドされていると、<xref:System.Windows.Forms.ToolStrip>をフォームに追加するコントロールは、保存、読み込みを含めるし、キャンセル ボタンに変更されます。

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>保存、読み込みを追加し、キャンセル BindingNavigator コンポーネントにボタン

1. Visual Studio で、追加、<xref:System.Windows.Forms.TextBox>をフォームにコントロール。

2. バインドする<xref:System.Windows.Forms.BindingSource>、データ ソースにバインドされます。 この例で、<xref:System.Windows.Forms.BindingSource>データベースにバインドされます。

3. データセットとテーブルのアダプターが生成されると、ドラッグ、<xref:System.Windows.Forms.BindingNavigator>コントロールをフォームにします。

4. 設定、<xref:System.Windows.Forms.BindingNavigator>コントロールの<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>プロパティを<xref:System.Windows.Forms.BindingSource>コントロールにバインドされている形式にします。

5. <xref:System.Windows.Forms.BindingNavigator> コントロールを選択します。

6. スマート タグ グリフをクリックします (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ため、 **BindingNavigator タスク**ダイアログが表示され選択**アイテムの編集**.

     **Items コレクション エディター**が表示されます。

7. **Items コレクション エディター**を次の手順します。

    1. 追加、<xref:System.Windows.Forms.ToolStripSeparator>と 3 つ<xref:System.Windows.Forms.ToolStripButton>を適切な種類の選択項目<xref:System.Windows.Forms.ToolStripItem>クリックして、**追加**ボタン。

    2. 設定、<xref:System.Windows.Forms.ToolStripItem.Name%2A>プロパティをボタンの**LoadButton**、 **SaveButton**、および**CancelButton**、それぞれします。

    3. 設定、<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティをボタンの**ロード**、**保存**と**キャンセル**します。

    4. 設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>ボタンの各プロパティ**テキスト**します。 このプロパティを設定する代わりに、**イメージ**または**ImageAndText**に表示されるイメージを設定し、<xref:System.Windows.Forms.ToolStripItem.Image%2A>プロパティ。

    5. クリックして**OK**ダイアログ ボックスを閉じます。ボタンに追加されて、<xref:System.Windows.Forms.ToolStrip>します。

8. フォームを右クリックし **コードの表示**します。

9. コード エディターでは、テーブル アダプターにデータを読み込むコードの行を見つけます。 このコードは、手順 2 でのデータ バインディングを設定するときに生成されました。 コードは、次のようになります:`TableAdapterName.Fill(DataSetName.TableName)`します。 ほとんどは、フォームのいる可能性がある<xref:System.Windows.Forms.Form.Load>イベント。

10. イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**ロード**<xref:System.Windows.Forms.ToolStripButton>以前に作成し、このデータ読み込みコードを移動します。

     コードは、次のようになります。

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

11. イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**保存**<xref:System.Windows.Forms.ToolStripButton>前に作成され、テーブル コントロール内のデータを更新するコードを記述にバインドします。

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
    > 場合によってで、<xref:System.Windows.Forms.BindingNavigator>コンポーネントが既に、**保存**Windows フォーム デザイナーによって生成されたコードではなく、ボタンをクリックします。 ここで上記のコードを配置することができます、<xref:System.Windows.Forms.ToolStripItem.Click>で、まったく新しいボタンを作成するのではなく、そのボタンのイベント ハンドラー、<xref:System.Windows.Forms.ToolStrip>します。 ボタンが既定では、無効になりますので、設定する必要があります、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>プロパティをボタンの`true`ボタンの機能を正しくが。

12. イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**キャンセル**<xref:System.Windows.Forms.ToolStripButton>以前に作成し、表示されるデータのレコードに変更をキャンセルするコードを記述します。

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
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>メソッドのスコープは、データの行にします。 次のレコードに移動する前に個々 のレコードを表示中に加えたあらゆる変更を保存します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
- [BindingSource コンポーネントの概要](bindingsource-component-overview.md)

---
title: '方法: 既存の Windows フォーム コントロールから継承する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0571bd6b169b94b1626bffb0d0793bbb22a93ba0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015864"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>方法: 既存の Windows フォーム コントロールから継承する

既存のコントロールの機能を拡張する場合は、継承によって既存のコントロールから派生したコントロールを作成できます。 既存のコントロールから継承すると、そのコントロールのすべての機能およびビジュアル プロパティが引き継がれます。 たとえば、から<xref:System.Windows.Forms.Button>継承されたコントロールを作成した場合、新しいコントロールは標準<xref:System.Windows.Forms.Button>コントロールとまったく同じように見え、動作します。 その後で、カスタム メソッドやカスタム プロパティの実装によって、新しいコントロールの機能を拡張または変更できます。 一部のコントロールでは、 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドをオーバーライドすることによって、継承されたコントロールの外観を変更することもできます。

## <a name="to-create-an-inherited-control"></a>継承したコントロールを作成するには

1. Visual Studio で、新しい**Windows フォームアプリケーション**プロジェクトを作成します。

2. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

3. **[新しい項目の追加]** ダイアログ ボックスの **[カスタム コントロール]** をダブルクリックします。

     新しいカスタム コントロールがプロジェクトに追加されます。

4. 以下を使用する場合:

   - Visual Basic、**ソリューションエクスプローラー**の上部にある **[すべてのファイルを表示]** をクリックします。 CustomControl1.vb を展開し、コード エディターで CustomControl1.Designer.vb を開きます。
   - C#で、コードエディターで CustomControl1.cs を開きます。

6. から<xref:System.Windows.Forms.Control>継承するクラス宣言を探します。

7. 基底クラスを継承元のコントロールに変更します。

     たとえば、から<xref:System.Windows.Forms.Button>継承する場合は、クラスの宣言を次のように変更します。

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. Visual Basic を使用している場合は、CustomControl1.Designer.vb を保存して閉じます。 コード エディターで CustomControl1.vb を開きます。

9. コントロールに組み込むカスタム メソッドやカスタム プロパティを実装します。

10. コントロールのグラフィカルな外観を変更する場合は、 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドをオーバーライドします。

    > [!NOTE]
    > を<xref:System.Windows.Forms.Control.OnPaint%2A>オーバーライドしても、すべてのコントロールの外観を変更することはできません。 Windows によって実行されるすべての描画 (たとえば、 <xref:System.Windows.Forms.TextBox>) を持つコントロールは、 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドを呼び出すことがないため、カスタムコードは使用されません。 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドが使用可能かどうかを確認するには、変更する特定のコントロールのヘルプドキュメントを参照してください。 すべての Windows フォーム コントロールの一覧については、「[Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)」を参照してください。 コントロールがメンバーメソッドとし<xref:System.Windows.Forms.Control.OnPaint%2A>てリストされていない場合は、このメソッドをオーバーライドすることによって外観を変更することはできません。 カスタム描画の詳細については、「[コントロールのカスタム描画およびレンダリング](custom-control-painting-and-rendering.md)」を参照してください。

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

11. コントロールを保存して、動作確認を行います。

## <a name="see-also"></a>関連項目

- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
- [方法: コントロールクラスから継承する](how-to-inherit-from-the-control-class.md)
- [方法: UserControl クラスを継承する](how-to-inherit-from-the-usercontrol-class.md)
- [方法: Windows フォームの作成者コントロール](how-to-author-controls-for-windows-forms.md)
- [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [チュートリアル: Windows フォームコントロールからの継承](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

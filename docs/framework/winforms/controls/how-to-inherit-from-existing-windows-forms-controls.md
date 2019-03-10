---
title: '方法: 継承可能な既存の Windows フォーム コントロール'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 9b3b5b2420a1121be81bc299dea645051f941cd8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707977"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>方法: 継承可能な既存の Windows フォーム コントロール
既存のコントロールの機能を拡張する場合は、継承によって既存のコントロールから派生したコントロールを作成できます。 既存のコントロールから継承すると、そのコントロールのすべての機能およびビジュアル プロパティが引き継がれます。 継承するコントロールを作成する場合など<xref:System.Windows.Forms.Button>は、新しいコントロールになります、act とまったく同じ標準<xref:System.Windows.Forms.Button>コントロール。 その後で、カスタム メソッドやカスタム プロパティの実装によって、新しいコントロールの機能を拡張または変更できます。 一部のコントロールで変更することできますも継承されたコントロールの外観をオーバーライドしてその<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-an-inherited-control"></a>継承したコントロールを作成するには  
  
1.  新しい **Windows フォーム アプリケーション プロジェクト**を作成します。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
3.  **[新しい項目の追加]** ダイアログ ボックスの **[カスタム コントロール]** をダブルクリックします。  
  
     新しいカスタム コントロールがプロジェクトに追加されます。  
  
4.  Visual Basic を使用している場合は、**ソリューション エクスプローラー**の上部にある **[すべてのファイルを表示]** をクリックします。 CustomControl1.vb を展開し、コード エディターで CustomControl1.Designer.vb を開きます。  
  
5.  C# を使用している場合は、コード エディターで CustomControl1.cs を開きます。  
  
6.  継承されるクラス宣言を見つけます<xref:System.Windows.Forms.Control>します。  
  
7.  基底クラスを継承元のコントロールに変更します。  
  
     継承したい場合など<xref:System.Windows.Forms.Button>、クラス宣言を次に変更します。  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Visual Basic を使用している場合は、CustomControl1.Designer.vb を保存して閉じます。 コード エディターで CustomControl1.vb を開きます。  
  
9. コントロールに組み込むカスタム メソッドやカスタム プロパティを実装します。  
  
10. コントロールの外観を変更する場合は、オーバーライド、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。  
  
    > [!NOTE]
    >  オーバーライドする<xref:System.Windows.Forms.Control.OnPaint%2A>すべてのコントロールの外観を変更することはできません。 これらのコントロールを持つすべての描画が Windows によって行われます (たとえば、 <xref:System.Windows.Forms.TextBox>) 呼び出すことはありません、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド、なり、決して使用して、カスタム コード。 かどうかを変更する特定のコントロールのヘルプ ドキュメントを参照してください、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドを使用できます。 すべての Windows フォーム コントロールの一覧については、「[Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)」を参照してください。 コントロールがない場合<xref:System.Windows.Forms.Control.OnPaint%2A>メンバー メソッドとして一覧に表示できない外観を変更するこのメソッドをオーバーライドすることで。 カスタム描画の詳細については、「[コントロールのカスタム描画およびレンダリング](custom-control-painting-and-rendering.md)」を参照してください。  
  
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
- [方法: コントロール クラスから継承します。](how-to-inherit-from-the-control-class.md)
- [方法: UserControl クラスを継承します。](how-to-inherit-from-the-usercontrol-class.md)
- [方法: Windows フォームのコントロールの作成](how-to-author-controls-for-windows-forms.md)
- [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [チュートリアル: Visual Basic による Windows フォーム コントロールから継承します。](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [チュートリアル: ビジュアルを含む Windows フォーム コントロールからの継承C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

---
title: '方法: 分割ウィンドウでのサイズ変更および位置指定動作を定義する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 8cdcfdfaa135a92ed6a6e96d4a72de2c97f2493d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328674"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>方法: 分割ウィンドウでのサイズ変更および位置指定動作を定義する
パネル、<xref:System.Windows.Forms.SplitContainer>コントロールを起こすもされているサイズを変更して、ユーザーによって操作します。 ただし、するは、スプリッターをプログラムで制御する場合は、場所が配置されているし、移動できるどの程度までです。  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>プロパティおよびその他のプロパティを<xref:System.Windows.Forms.SplitContainer>コントロールは、ニーズに合わせてユーザー インターフェイスの動作をより正確に制御を提供します。 これらのプロパティは、次の表に一覧表示されます。  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property|分割線をキーボードやマウスを使用して移動可能なかどうかを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property|移動可能な分割バーを左端または上端からのピクセル単位で距離を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property|最小距離 (ピクセル単位)、スプリッターをユーザーが移動できることを決定します。|  
  
 次の例を変更、<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>プロパティを「分割線にスナップ」効果を作成、ユーザーは、分割線をドラッグと、に、既定値 1 ではなく、10 ピクセル単位で増加します。  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>SplitContainer サイズ変更動作を定義するには  
  
1. プロシージャでは、次のように設定します。、<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>目的のサイズにプロパティ 'スナップ' スプリッターの動作を実現できるようにします。  
  
     フォームの内で、次のコード例で<xref:System.Windows.Forms.Form.Load>イベント、内のスプリッター、<xref:System.Windows.Forms.SplitContainer>コントロールをドラッグすると、10 ピクセルのジャンプを設定します。  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     (Visual C#)イベント ハンドラーを登録するフォームのコンス トラクターでは、次のコードを配置します。  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     分割線の左側または右側に少し移動効果はありません厳しく;ただし、マウス ポインターでは、いずれかの方向に 10 ピクセルを移動、スプリッターが新しい位置にスナップされます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>

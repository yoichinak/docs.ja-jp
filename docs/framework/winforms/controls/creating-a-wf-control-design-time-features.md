---
title: 'チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
ms.openlocfilehash: c8d04725a576c9e24a4b7d4aec1251516a8c544c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666231"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成

カスタムコントロールのデザイン時のエクスペリエンスは、関連するカスタムデザイナーを作成することによって拡張できます。

このチュートリアルでは、カスタムコントロールのカスタムデザイナーを作成する方法について説明します。 `MarqueeControl`型と、それに関連付けられたデザイナークラス`MarqueeControlRootDesigner`(と呼ばれる) を実装します。

この`MarqueeControl`型は、シアターマーキーに似た表示を実装し、アニメーション化されたライトと点滅するテキストを使用します。

このコントロールのデザイナーは、デザイン時のカスタムエクスペリエンスを提供するために、デザイン環境と対話します。 カスタムデザイナーを使用すると、アニメーション化さ`MarqueeControl`れたライトと、さまざまな組み合わせで点滅するテキストを使用して、カスタム実装を組み立てることができます。 アセンブルされたコントロールは、他の Windows フォームコントロールと同様に、フォーム上で使用できます。

このチュートリアルでは、以下のタスクを行います。

- プロジェクトの作成

- コントロールライブラリプロジェクトの作成

- カスタムコントロールプロジェクトの参照

- カスタムコントロールとそのカスタムデザイナーの定義

- カスタムコントロールのインスタンスの作成

- デザイン時デバッグのためのプロジェクトの設定

- カスタムコントロールの実装

- カスタムコントロールの子コントロールの作成

- MarqueeBorder 子コントロールを作成する

- カスタムデザイナーを作成してプロパティをシャドウおよびフィルター処理する

- コンポーネントの変更の処理

- デザイナー動詞をカスタムデザイナーに追加する

- カスタム UITypeEditor の作成

- デザイナーでのカスタムコントロールのテスト

完了すると、カスタムコントロールは次のようになります。

![テキストと [開始] および [停止] ボタンを示すマーキーを表示するアプリ。](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

完全なコードリストについて[は、「方法:デザイン時機能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))を利用する Windows フォームコントロールを作成します。

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、Visual Studio が必要です。

## <a name="creating-the-project"></a>プロジェクトの作成

最初にアプリケーションのプロジェクトを作成します。 このプロジェクトは、カスタムコントロールをホストするアプリケーションをビルドするために使用します。

Visual Studio を開き、"MarqueeControlTest" という名前の Windows フォームアプリケーションプロジェクトを作成します (**ファイル** >  **新しい** > **プロジェクト** >  **ビジュアルC#**  または  **Visual Basic**  > **クラシックデスクトップ** **Windows フォームアプリケーション)。**  > 

## <a name="creating-a-control-library-project"></a>コントロールライブラリプロジェクトの作成

次の手順では、コントロールライブラリプロジェクトを作成します。 新しいカスタムコントロールとそれに対応するカスタムデザイナーを作成します。

### <a name="to-create-the-control-library-project"></a>コントロールライブラリプロジェクトを作成するには

1. ソリューションに Windows フォームコントロールライブラリプロジェクトを追加します。 プロジェクトに "MarqueeControlLibrary" という名前を指定します。

2. **ソリューションエクスプローラー**を使用して、選択した言語に応じて、"UserControl1.cs" または "UserControl1" という名前のソースファイルを削除して、プロジェクトの既定のコントロールを削除します。 詳細については、「[方法 :項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))を削除、削除、および除外します。

3. 新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクトに追加します。 新しいソースファイルに "MarqueeControl" のベース名を指定します。

4. **ソリューションエクスプローラー**を使用して、 `MarqueeControlLibrary`プロジェクトに新しいフォルダーを作成します。 詳細については、「[方法 :新しいプロジェクト項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))を追加します。 新しいフォルダーに「Design」という名前を指定します。

5. **Design**フォルダーを右クリックし、新しいクラスを追加します。 ソースファイルに "MarqueeControlRootDesigner" のベース名を指定します。

6. System.string アセンブリの型を使用する必要があるため、この参照をプロジェクトに追加し`MarqueeControlLibrary`てください。

    > [!NOTE]
    > System.servicemodel アセンブリを使用するには、プロジェクトで .NET Framework クライアントプロファイルではなく、完全バージョンの .NET Framework を対象にする必要があります。 ターゲットフレームワークを変更するには[、「方法:.NET Framework のターゲット バージョンを指定する](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)」を参照してください。

## <a name="referencing-the-custom-control-project"></a>カスタムコントロールプロジェクトの参照

カスタムコントロールをテスト`MarqueeControlTest`するには、プロジェクトを使用します。 `MarqueeControlLibrary`アセンブリにプロジェクト参照を追加すると、テストプロジェクトはカスタムコントロールを認識するようになります。

### <a name="to-reference-the-custom-control-project"></a>カスタムコントロールプロジェクトを参照するには

- プロジェクトで、 `MarqueeControlLibrary`アセンブリへのプロジェクト参照を追加します。 `MarqueeControlTest` `MarqueeControlLibrary`アセンブリを直接参照するのではなく、 **[参照の追加]** ダイアログボックスの **[プロジェクト]** タブを使用するようにしてください。

## <a name="defining-a-custom-control-and-its-custom-designer"></a>カスタムコントロールとそのカスタムデザイナーの定義
 カスタムコントロールは<xref:System.Windows.Forms.UserControl>クラスから派生します。 これにより、コントロールに他のコントロールを含めることができます。また、コントロールには、既定の機能が多数用意されています。

 カスタムコントロールには、関連付けられたカスタムデザイナーがあります。 これにより、カスタムコントロール専用にカスタマイズされた独自のデザインエクスペリエンスを作成できます。

 コントロールをデザイナーに関連付けるには、 <xref:System.ComponentModel.DesignerAttribute>クラスを使用します。 カスタムコントロールのデザイン時動作全体を開発しているため、カスタムデザイナーは<xref:System.ComponentModel.Design.IRootDesigner>インターフェイスを実装します。

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>カスタムコントロールとそのカスタムデザイナーを定義するには

1. `MarqueeControl` **コードエディター**でソースファイルを開きます。 ファイルの先頭に、次の名前空間をインポートします。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. をクラス`MarqueeControl`宣言に追加します。<xref:System.ComponentModel.DesignerAttribute> これにより、カスタムコントロールがデザイナーに関連付けられます。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. `MarqueeControlRootDesigner` **コードエディター**でソースファイルを開きます。 ファイルの先頭に、次の名前空間をインポートします。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <xref:System.Windows.Forms.Design.DocumentDesigner>クラスを継承する`MarqueeControlRootDesigner`ようにの宣言を変更します。 を適用して、デザイナーと**ツールボックス**の対話を指定します。 <xref:System.ComponentModel.ToolboxItemFilterAttribute>

     **メモ**`MarqueeControlRootDesigner`クラスの定義は、"MarqueeControlLibrary" という名前空間で囲まれています。 この宣言により、デザイン関連の型用に予約された特殊な名前空間にデザイナーが配置されます。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. `MarqueeControlRootDesigner`クラスのコンストラクターを定義します。 コンストラクター本体<xref:System.Diagnostics.Trace.WriteLine%2A>にステートメントを挿入します。 これは、デバッグのために役立ちます。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a>カスタムコントロールのインスタンスの作成
 コントロールのカスタムデザイン時の動作を確認するには、コントロールのインスタンスを project の`MarqueeControlTest`フォームに配置します。

### <a name="to-create-an-instance-of-your-custom-control"></a>カスタムコントロールのインスタンスを作成するには

1. 新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlTest`プロジェクトに追加します。 新しいソースファイルに "DemoMarqueeControl" のベース名を指定します。

2. `DemoMarqueeControl` **コードエディター**でファイルを開きます。 ファイルの先頭に、 `MarqueeControlLibrary`名前空間をインポートします。

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. `MarqueeControl`クラスを継承する`DemoMarqueeControl`ようにの宣言を変更します。

2. プロジェクトをビルドします。

3. Windows フォーム デザイナーで `Form1` を開きます。

4. **ツールボックス**の **[MarqueeControlTest Components]** タブを見つけて開きます。 `DemoMarqueeControl` **ツールボックス**からフォームにをドラッグします。

5. プロジェクトをビルドします。

## <a name="setting-up-the-project-for-design-time-debugging"></a>デザイン時デバッグのためのプロジェクトの設定

カスタムデザイン時のエクスペリエンスを開発する場合は、コントロールとコンポーネントをデバッグする必要があります。 デザイン時にデバッグを許可するようにプロジェクトを設定する簡単な方法があります。 詳細については、「[チュートリアル:デザイン時](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)にカスタム Windows フォームコントロールをデバッグする。

### <a name="to-set-up-the-project-for-design-time-debugging"></a>デザイン時デバッグ用にプロジェクトを設定するには

1. プロジェクトを右クリック`MarqueeControlLibrary`し、 **[プロパティ]** を選択します。

2. MarqueeControlLibrary プロパティページ ダイアログボックスで、**デバッグ** ページを選択します。

3. **[開始アクション]** セクションで、 **[外部プログラムの開始]** を選択します。 Visual studio の別のインスタンスをデバッグする場合は、省略記号 (![[visual](./media/visual-studio-ellipsis-button.png)studio のプロパティウィンドウ] の省略記号ボタン (...)) をクリックして、visual studio IDE を参照します。 実行可能ファイルの名前は devenv.exe で、を既定の場所にインストールした場合、パスは%programfiles%\Microsoft Visual Studio 9.0 \ Common7\IDE\devenv.exe. になります。

4. [OK] をクリックして、ダイアログボックスを閉じます。

5. プロジェクトを右クリック`MarqueeControlLibrary`し、[スタートアッププロジェクトに設定] を選択して、このデバッグ構成を有効にします。

## <a name="checkpoint"></a>チェックポイント

これで、カスタムコントロールのデザイン時動作をデバッグする準備ができました。 デバッグ環境が正しく設定されていることを確認したら、カスタムコントロールとカスタムデザイナーの関連付けをテストします。

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>デバッグ環境とデザイナーの関連付けをテストするには

1. **コードエディター**で<xref:System.Diagnostics.Trace.WriteLine%2A>ソースファイルを開き、ステートメントにブレークポイントを設定します。 `MarqueeControlRootDesigner`

2. F5 キーを押してデバッグセッションを開始します。 Visual Studio の新しいインスタンスが作成されることに注意してください。

3. Visual Studio の新しいインスタンスで、"MarqueeControlTest" ソリューションを開きます。 **[ファイル]** メニューから **[最近使ったプロジェクト]** を選択すると、ソリューションを簡単に見つけることができます。 "MarqueeControlTest" ソリューションファイルは、最近使用したファイルとして一覧表示されます。

4. デザイナーで`DemoMarqueeControl`を開きます。 Visual Studio のデバッグインスタンスがフォーカスを取得し、ブレークポイントで実行を停止することに注意してください。 F5 キーを押してデバッグセッションを続行します。

この時点で、カスタムコントロールとそれに関連付けられているカスタムデザイナーを開発およびデバッグするために、すべてが準備されています。 このチュートリアルの残りの部分では、コントロールとデザイナーの機能を実装する方法の詳細について説明します。

## <a name="implementing-your-custom-control"></a>カスタムコントロールの実装

は、カスタマイズ<xref:System.Windows.Forms.UserControl> が少ししかないです。`MarqueeControl` ここでは、2 `Start`つのメソッドを公開してい`Stop`ます。は、マーキーアニメーションを開始し、はアニメーションを停止します。 には`MarqueeControl` 、 `IMarqueeWidget`インターフェイス`StopMarquee` `Stop`を実装する子コントロールが含まれて`StartMarquee` おり、各子コントロールを列挙し、それぞれの子コントロールでメソッドとメソッドをそれぞれ呼び出します。`Start`を実装`IMarqueeWidget`する。

コントロール`MarqueeBorder` <xref:System.Windows.Forms.Control.OnLayout%2A>と`MarqueeText`コントロールの外観は、レイアウトに依存している`MarqueeControl`ため、メソッドをオーバーライド<xref:System.Windows.Forms.Control.PerformLayout%2A>し、この型の子コントロールに対してを呼び出します。

これは`MarqueeControl`カスタマイズの範囲です。 実行時の機能は`MarqueeBorder`コントロールと`MarqueeText`コントロールによって実装され、デザイン時の`MarqueeBorderDesigner`機能はクラスおよび`MarqueeControlRootDesigner`クラスによって実装されます。

### <a name="to-implement-your-custom-control"></a>カスタムコントロールを実装するには

1. `MarqueeControl` **コードエディター**でソースファイルを開きます。 `Start`メソッドと`Stop`メソッドを実装します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <xref:System.Windows.Forms.Control.OnLayout%2A> メソッドをオーバーライドします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a>カスタムコントロールの子コントロールの作成

は`MarqueeControl` 、 `MarqueeBorder`コントロールと`MarqueeText`コントロールという2種類の子コントロールをホストします。

- `MarqueeBorder`:このコントロールは、端の周りに "ライト" の境界線を描画します。 ライトが連続して点滅しているように見えます。 ライトフラッシュがという`UpdatePeriod`プロパティによって制御される速度。 他のいくつかのカスタムプロパティによって、コントロールの外観の他の側面が決まります。 `StartMarquee` と`StopMarquee`呼ばれる2つのメソッドは、アニメーションの開始と停止を制御します。

- `MarqueeText`:このコントロールは、点滅する文字列を描画します。 コントロールと同様に、テキストが点滅する速度は、 `UpdatePeriod`プロパティによって制御されます。 `MarqueeBorder` コントロールには`StopMarquee` 、コントロール`MarqueeBorder`に共通のメソッド`StartMarquee`とメソッドもあります。 `MarqueeText`

デザイン時`MarqueeControlRootDesigner`に、を使用すると、これら2つのコントロール型`MarqueeControl`を任意の組み合わせでに追加できます。

2つのコントロールの共通機能は、と呼ばれる`IMarqueeWidget`インターフェイスに分けられています。 これにより`MarqueeControl` 、は、マーキーに関連する子コントロールを検出し、特別な処理を行うことができます。

定期的なアニメーション機能を実装するには、 <xref:System.ComponentModel.BackgroundWorker>名前空間の<xref:System.ComponentModel?displayProperty=nameWithType>オブジェクトを使用します。 オブジェクトを使用<xref:System.Windows.Forms.Timer>することもできます`IMarqueeWidget`が、多くのオブジェクトが存在する場合、1つの UI スレッドがアニメーションを維持できないことがあります。

### <a name="to-create-a-child-control-for-your-custom-control"></a>カスタムコントロールの子コントロールを作成するには

1. 新しいクラス項目を`MarqueeControlLibrary`プロジェクトに追加します。 新しいソースファイルに "IMarqueeWidget" のベース名を指定します。

2. **コードエディター**で`class` `interface`ソースファイルを開き、宣言をからに変更します。 `IMarqueeWidget`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. 次のコードを`IMarqueeWidget`インターフェイスに追加して、2つのメソッドと、マーキーアニメーションを操作するプロパティを公開します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. 新しい**カスタムコントロール**項目を`MarqueeControlLibrary`プロジェクトに追加します。 新しいソースファイルに "MarqueeText" のベース名を指定します。

5. コンポーネントを<xref:System.ComponentModel.BackgroundWorker> **ツールボックス**からコントロールにドラッグします。`MarqueeText` このコンポーネントを使用する`MarqueeText`と、コントロール自体を非同期的に更新できます。

6. プロパティウィンドウで、 <xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgress`プロパティと<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティをに`true`設定します。 これらの設定に<xref:System.ComponentModel.BackgroundWorker>より、コンポーネントは定期的<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>にイベントを発生させ、非同期更新を取り消すことができます。 詳細については、「 [BackgroundWorker Component](backgroundworker-component.md)」を参照してください。

7. `MarqueeText` **コードエディター**でソースファイルを開きます。 ファイルの先頭に、次の名前空間をインポートします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. を`MarqueeText` 継承し、`IMarqueeWidget`インターフェイスを実装するように、の宣言を変更します。<xref:System.Windows.Forms.Label>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. 公開されたプロパティに対応するインスタンス変数を宣言し、コンストラクターで初期化します。 フィールド`isLit`は、 `LightColor`プロパティによって指定された色でテキストを描画するかどうかを決定します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. `IMarqueeWidget` インターフェイスを実装します。

    メソッド`StartMarquee`と<xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>メソッドは、コンポーネントのメソッド<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>とメソッドを呼び出して、アニメーションを開始および停止します。 `StopMarquee`

    属性と属性<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>はプロパティに適用されるため、"Marquee"と呼ばれるプロパティウィンドウのカスタムセクションに表示されます。`UpdatePeriod` <xref:System.ComponentModel.CategoryAttribute.Category%2A>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. プロパティアクセサーを実装します。 クライアント`LightColor`には、と`DarkColor`の2つのプロパティを公開します。 これらの<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>プロパティには属性と属性が適用されるので、プロパティは"Marquee"と呼ばれるプロパティウィンドウのカスタムセクションに表示されます。<xref:System.ComponentModel.CategoryAttribute.Category%2A>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <xref:System.ComponentModel.BackgroundWorker>コンポーネントとイベント<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>のハンドラーを実装します。 <xref:System.ComponentModel.BackgroundWorker.DoWork>

    イベント<xref:System.ComponentModel.BackgroundWorker.DoWork>ハンドラーは、によって`UpdatePeriod`指定されたミリ秒数<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>の間スリープ状態になり、コードがを<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>呼び出すことによってアニメーションを停止するまで、イベントを発生させます。

    イベント<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>ハンドラーは、テキストを淡色と濃色の状態の間で切り替えて、点滅のようにします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. アニメーションを<xref:System.Windows.Forms.Control.OnPaint%2A>有効にするには、メソッドをオーバーライドします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. F6 キーを押してソリューションをビルドします。

## <a name="create-the-marqueeborder-child-control"></a>MarqueeBorder 子コントロールを作成する

コントロール`MarqueeBorder`は、 `MarqueeText`コントロールよりも少し洗練されています。 これにはさらに多くのプロパティが<xref:System.Windows.Forms.Control.OnPaint%2A>あり、メソッドのアニメーションも複雑になります。 原則として、 `MarqueeText`コントロールと非常によく似ています。

コントロールは`MarqueeBorder`子コントロールを持つことができるため、 <xref:System.Windows.Forms.Control.Layout>イベントに注意する必要があります。

### <a name="to-create-the-marqueeborder-control"></a>MarqueeBorder コントロールを作成するには

1. 新しい**カスタムコントロール**項目を`MarqueeControlLibrary`プロジェクトに追加します。 新しいソースファイルに "MarqueeBorder" のベース名を指定します。

2. コンポーネントを<xref:System.ComponentModel.BackgroundWorker> **ツールボックス**からコントロールにドラッグします。`MarqueeBorder` このコンポーネントを使用する`MarqueeBorder`と、コントロール自体を非同期的に更新できます。

3. プロパティウィンドウで、 <xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgress`プロパティと<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティをに`true`設定します。 これらの設定に<xref:System.ComponentModel.BackgroundWorker>より、コンポーネントは定期的<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>にイベントを発生させ、非同期更新を取り消すことができます。 詳細については、「 [BackgroundWorker Component](backgroundworker-component.md)」を参照してください。

4. プロパティウィンドウで、[イベント] ボタンをクリックします。 イベント<xref:System.ComponentModel.BackgroundWorker.DoWork> および<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントのハンドラーをアタッチします。

5. `MarqueeBorder` **コードエディター**でソースファイルを開きます。 ファイルの先頭に、次の名前空間をインポートします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. から`IMarqueeWidget` `MarqueeBorder` 継承し、インターフェイスを実装するように、の宣言を変更します。<xref:System.Windows.Forms.Panel>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. `MarqueeBorder`コントロールの状態を管理するための2つ`MarqueeSpinDirection`の列挙体を宣言します。これは、ライトが境界の周りを`MarqueeLightShape`"スピン" する方向を決定します。は、ライトの形状 (正方形または円形) を決定します。 これらの宣言は、 `MarqueeBorder`クラス宣言の前に配置します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. 公開されたプロパティに対応するインスタンス変数を宣言し、コンストラクターで初期化します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. `IMarqueeWidget` インターフェイスを実装します。

    メソッド`StartMarquee`と<xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>メソッドは、コンポーネントのメソッド<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>とメソッドを呼び出して、アニメーションを開始および停止します。 `StopMarquee`

    コントロールに`MarqueeBorder`子コントロールを含めることができる`StartMarquee`ため、メソッドは、すべての`StartMarquee`子コントロールを列挙`IMarqueeWidget`し、を実装する子コントロールに対してを呼び出します。 `StopMarquee`メソッドには同様の実装があります。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. プロパティアクセサーを実装します。 コントロール`MarqueeBorder`には、外観を制御するためのプロパティがいくつかあります。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <xref:System.ComponentModel.BackgroundWorker>コンポーネントとイベント<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>のハンドラーを実装します。 <xref:System.ComponentModel.BackgroundWorker.DoWork>

    イベント<xref:System.ComponentModel.BackgroundWorker.DoWork>ハンドラーは、によって`UpdatePeriod`指定されたミリ秒数<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>の間スリープ状態になり、コードがを<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>呼び出すことによってアニメーションを停止するまで、イベントを発生させます。

    イベント<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>ハンドラーは、他のライトの明るい/暗い状態が決定される "基本" ライトの位置をインクリメントし、 <xref:System.Windows.Forms.Control.Refresh%2A>メソッドを呼び出して、コントロール自体を再描画します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. ヘルパーメソッドと`IsLit` `DrawLight`を実装します。

    メソッド`IsLit`は、指定された位置のライトの色を決定します。 "Lit" のライトは、 `LightColor`プロパティによって指定された色で描画されます。 "ダーク" は、 `DarkColor`プロパティによって指定された色で描画されます。

    メソッド`DrawLight`は、適切な色、形状、および位置を使用してライトを描画します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <xref:System.Windows.Forms.Control.OnLayout%2A>メソッドと<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドをオーバーライドします。

    メソッド<xref:System.Windows.Forms.Control.OnPaint%2A>は、 `MarqueeBorder`コントロールの端に沿ってライトを描画します。

    メソッドは<xref:System.Windows.Forms.Control.OnPaint%2A> `MarqueeBorder`コントロールのディメンションに依存するため、レイアウトが変更されるたびに呼び出す必要があります。 これを実現するに<xref:System.Windows.Forms.Control.OnLayout%2A>は、 <xref:System.Windows.Forms.Control.Refresh%2A>をオーバーライドし、を呼び出します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>カスタムデザイナーを作成してプロパティをシャドウおよびフィルター処理する

クラス`MarqueeControlRootDesigner`は、ルートデザイナーの実装を提供します。 で`MarqueeControl`動作するこのデザイナーに加えて、 `MarqueeBorder`コントロールに特に関連付けられたカスタムデザイナーが必要になります。 このデザイナーには、カスタムルートデザイナーのコンテキストに適したカスタム動作が用意されています。

具体的には`MarqueeBorderDesigner` 、は、 `MarqueeBorder`コントロールの特定のプロパティを "シャドウ" してフィルター処理し、デザイン環境との相互作用を変更します。

コンポーネントのプロパティアクセサーへの呼び出しのインターセプトは、"シャドウ処理" と呼ばれます。 これにより、デザイナーはユーザーが設定した値を追跡し、必要に応じてその値をデザイン対象のコンポーネントに渡すことができます。

この例<xref:System.Windows.Forms.Control.Visible%2A>では、プロパティ<xref:System.Windows.Forms.Control.Enabled%2A>とプロパティがによって`MarqueeBorderDesigner`シャドウされます。これにより`MarqueeBorder` 、デザイン時にユーザーがコントロールを非表示にしたり無効にしたりすることができなくなります。

デザイナーでは、プロパティを追加および削除することもできます。 この例<xref:System.Windows.Forms.Control.Padding%2A>では、プロパティはデザイン時に削除されます。 `MarqueeBorder`コントロールはプログラムによって、 `LightSize`プロパティによって指定されたライトのサイズに基づいて余白を設定します。

の基本クラスは`MarqueeBorderDesigner`です<xref:System.ComponentModel.Design.ComponentDesigner>。これには、デザイン時にコントロールによって公開される属性、プロパティ、およびイベントを変更するためのメソッドがあります。

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

これらのメソッドを使用してコンポーネントのパブリックインターフェイスを変更する場合は、次の規則に従う必要があります。

- メソッドでのみ項目を追加`PreFilter`または削除する

- メソッド内の既存の`PostFilter`項目のみを変更する

- 常に基本実装を`PreFilter`メソッドで呼び出す

- `PostFilter`メソッドの最後に基本実装を呼び出します。

これらの規則に従うことで、デザイン時環境のすべてのデザイナーが、デザインされているすべてのコンポーネントの一貫したビューを確実に表示できるようになります。

クラス<xref:System.ComponentModel.Design.ComponentDesigner>は、シャドウプロパティの値を管理するためのディクショナリを提供します。これにより、特定のインスタンス変数を作成する必要がなくなります。

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>プロパティをシャドウおよびフィルター処理するためのカスタムデザイナーを作成するには

1. **Design**フォルダーを右クリックし、新しいクラスを追加します。 ソースファイルに "MarqueeBorderDesigner" のベース名を指定します。

2. `MarqueeBorderDesigner` **コードエディター**でソースファイルを開きます。 ファイルの先頭に、次の名前空間をインポートします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. `MarqueeBorderDesigner` を<xref:System.Windows.Forms.Design.ParentControlDesigner>継承するようにの宣言を変更します。

    コントロールに`MarqueeBorder`子コントロールを含めることが`MarqueeBorderDesigner`できるため<xref:System.Windows.Forms.Design.ParentControlDesigner>、はを継承します。これは、親子の相互作用を処理します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. の<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>基本実装をオーバーライドします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <xref:System.Windows.Forms.Control.Enabled%2A> プロパティと <xref:System.Windows.Forms.Control.Visible%2A> プロパティを実装します。 これらの実装は、コントロールのプロパティをシャドウします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a>コンポーネントの変更の処理
 クラス`MarqueeControlRootDesigner`は、 `MarqueeControl`インスタンスのカスタムデザイン時エクスペリエンスを提供します。 デザイン時の機能のほとんどは<xref:System.Windows.Forms.Design.DocumentDesigner>クラスから継承されています。コードでは、コンポーネントの変更の処理とデザイナー動詞の追加という2つのカスタマイズのカスタマイズを実装します。

 ユーザーが`MarqueeControl`インスタンスをデザイン`MarqueeControl`すると、ルートデザイナーはとその子コントロールに対する変更を追跡します。 デザイン時環境には、コンポーネントの状態に<xref:System.ComponentModel.Design.IComponentChangeService>対する変更を追跡するための便利なサービスが用意されています。

 このサービスへの参照を取得するには、 <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>メソッドを使用して環境に対してクエリを実行します。 クエリが成功した場合、デザイナーは<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>イベントのハンドラーをアタッチし、デザイン時に一貫性のある状態を維持するために必要なすべてのタスクを実行できます。

 `MarqueeControlRootDesigner`クラスの場合は、 <xref:System.Windows.Forms.Control.Refresh%2A> `IMarqueeWidget` に格納されている各オブジェクトに対してメソッド`MarqueeControl`を呼び出します。 これにより、 `IMarqueeWidget`親の<xref:System.Windows.Forms.Control.Size%2A>ようなプロパティが変更されたときに、オブジェクトが適切に再描画されます。

### <a name="to-handle-component-changes"></a>コンポーネントの変更を処理するには

1. **コードエディター**で<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>ソースファイルを開き、メソッドをオーバーライドします。 `MarqueeControlRootDesigner` の<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>基本実装を呼び出し、に<xref:System.ComponentModel.Design.IComponentChangeService>対してクエリを実行します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. イベントハンドラー <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>を実装します。 送信コンポーネントの型をテストし、が`IMarqueeWidget`の場合は、その<xref:System.Windows.Forms.Control.Refresh%2A>メソッドを呼び出します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a>デザイナー動詞をカスタムデザイナーに追加する

デザイナー動詞は、イベントハンドラーにリンクされたメニューコマンドです。 デザイナー動詞は、デザイン時にコンポーネントのショートカットメニューに追加されます。 詳細については、「 <xref:System.ComponentModel.Design.DesignerVerb> 」を参照してください。

デザイナーには、次の2つのデザイナー動詞を追加します。**テストを実行**し、**テストを停止**します。 これらの動詞を使用すると、 `MarqueeControl`デザイン時にの実行時の動作を表示できます。 これらの`MarqueeControlRootDesigner`動詞はに追加されます。

**実行テスト**が呼び出されると、動詞イベントハンドラーはに対し`StartMarquee` `MarqueeControl`てメソッドを呼び出します。 **停止テスト**が呼び出されると、動詞イベントハンドラーはに対し`StopMarquee` `MarqueeControl`てメソッドを呼び出します。 メソッド`StartMarquee`と`StopMarquee`メソッドの実装では、を実装`IMarqueeWidget`する含まれるコントロールに対してこれら`IMarqueeWidget`のメソッドを呼び出します。これにより、含まれるコントロールもテストに参加します。

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>デザイナー動詞をカスタムデザイナーに追加するには

1. クラスで、およびと`OnVerbStopTest`いう名前`OnVerbRunTest`のイベントハンドラーを追加します。 `MarqueeControlRootDesigner`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. これらのイベントハンドラーを、対応するデザイナー動詞に接続します。 `MarqueeControlRootDesigner`基底クラス<xref:System.ComponentModel.Design.DesignerVerbCollection>からを継承します。 2つの新しい<xref:System.ComponentModel.Design.DesignerVerb>オブジェクトを作成し、 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>メソッドでこのコレクションに追加します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a>カスタム UITypeEditor の作成

ユーザーに対してカスタムのデザイン時エクスペリエンスを作成する場合、多くの場合、プロパティウィンドウとのカスタム操作を作成することをお勧めします。 これを行うには、を<xref:System.Drawing.Design.UITypeEditor>作成します。 詳細については、「[方法 :UI 型エディター](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120))を作成します。

コントロール`MarqueeBorder`は、プロパティウィンドウ内のいくつかのプロパティを公開します。 これらのプロパティのうち`MarqueeSpinDirection`の`MarqueeLightShape` 2 つは、列挙体によって表されます。 UI 型エディターの使用方法を示すために、 `MarqueeLightShape`プロパティにはクラスが<xref:System.Drawing.Design.UITypeEditor>関連付けられています。

### <a name="to-create-a-custom-ui-type-editor"></a>カスタム UI 型エディターを作成するには

1. `MarqueeBorder` **コードエディター**でソースファイルを開きます。

2. `MarqueeBorder`クラスの定義で、から<xref:System.Drawing.Design.UITypeEditor>派生するという`LightShapeEditor`クラスを宣言します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. という<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>名前`editorService`のインスタンス変数を宣言します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> メソッドをオーバーライドします。 この実装は<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>を返します。これは、 `LightShapeEditor`を表示する方法をデザイン環境に指示します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> メソッドをオーバーライドします。 この実装は、 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService>オブジェクトのデザイン環境に対してクエリを行います。 成功した場合は、 `LightShapeSelectionControl`が作成されます。 を開始するために<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>メソッドが呼び出されます。 `LightShapeEditor` この呼び出しからの戻り値がデザイン環境に返されます。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>カスタム UITypeEditor のビューコントロールの作成

1. プロパティ`MarqueeLightShape`は、 `Square`と`Circle`の2種類のライトシェイプをサポートしています。 プロパティウィンドウでこれらの値をグラフィカルに表示する目的でのみ使用されるカスタムコントロールを作成します。 このカスタムコントロールは、プロパティウィンドウと対話<xref:System.Drawing.Design.UITypeEditor>するためにによって使用されます。

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>カスタム UI 型エディターのビューコントロールを作成するには

1. 新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクトに追加します。 新しいソースファイルに "LightShapeSelectionControl" のベース名を指定します。

2. **ツールボックス**からに2つ<xref:System.Windows.Forms.Panel>のコントロールをドラッグします。`LightShapeSelectionControl` とという`circlePanel`名前を指定します。 `squarePanel` それらを並べて配置します。 <xref:System.Windows.Forms.Control.Size%2A> 両方<xref:System.Windows.Forms.Panel>のコントロールのプロパティを (60, 60) に設定します。 コントロールのプロパティを (8, 10) に設定します。 <xref:System.Windows.Forms.Control.Location%2A> `squarePanel` コントロールのプロパティを (80, 10) に設定します。 <xref:System.Windows.Forms.Control.Location%2A> `circlePanel` 最後に、 `LightShapeSelectionControl`の<xref:System.Windows.Forms.Control.Size%2A>プロパティを (150, 80) に設定します。

3. `LightShapeSelectionControl` **コードエディター**でソースファイルを開きます。 ファイルの先頭に、 <xref:System.Windows.Forms.Design?displayProperty=nameWithType>名前空間をインポートします。

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. コントロール<xref:System.Windows.Forms.Control.Click> `squarePanel`とコントロール`circlePanel`のイベントハンドラーを実装します。 これらのメソッド<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>は、カスタム<xref:System.Drawing.Design.UITypeEditor>編集セッションを終了するためにを呼び出します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. という<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>名前`editorService`のインスタンス変数を宣言します。

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. という`MarqueeLightShape`名前`lightShapeValue`のインスタンス変数を宣言します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. <xref:System.Windows.Forms.Control.Click> コンストラクターで`squarePanel` 、イベント`circlePanel` ハンドラー<xref:System.Windows.Forms.Control.Click>をとコントロールのイベントにアタッチします。 `LightShapeSelectionControl` また、デザイン環境から`MarqueeLightShape` `lightShapeValue`フィールドに値を割り当てるコンストラクターのオーバーロードを定義します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. メソッドで、 <xref:System.Windows.Forms.Control.Click>イベントハンドラーをデタッチします。 <xref:System.ComponentModel.Component.Dispose%2A>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. **ソリューション エクスプローラー**で、 **[すべてのファイルを表示]** ボタンをクリックします。 LightShapeSelectionControl.Designer.cs または LightShapeSelectionControl ファイルを開き、 <xref:System.ComponentModel.Component.Dispose%2A>メソッドの既定の定義を削除します。

5. `LightShape` プロパティを実装します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。 この実装では、塗りつぶされた正方形と円を描画します。 また、1つの図形の周りに境界線を描画して、選択された値を強調表示します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a>デザイナーでのカスタムコントロールのテスト

この時点で、 `MarqueeControlLibrary`プロジェクトをビルドできます。 `MarqueeControl`クラスを継承し、フォームで使用するコントロールを作成して、実装をテストします。

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>カスタムの MarqueeControl 実装を作成するには

1. Windows フォーム デザイナーで `DemoMarqueeControl` を開きます。 これにより、 `DemoMarqueeControl`型のインスタンスが作成され、 `MarqueeControlRootDesigner`型のインスタンスに表示されます。

2. **ツールボックス**で、 **[MarqueeControlLibrary Components]** タブを開きます。選択できるコントロールと`MarqueeBorder` `MarqueeText`コントロールが表示されます。

3. `MarqueeBorder`コントロールのインスタンスを`DemoMarqueeControl`デザインサーフェイスにドラッグします。 この`MarqueeBorder`コントロールを親コントロールにドッキングします。

4. `MarqueeText`コントロールのインスタンスを`DemoMarqueeControl`デザインサーフェイスにドラッグします。

5. ソリューションをビルドします。

6. を右クリック`DemoMarqueeControl`し、ショートカットメニューの **[テストの実行]** オプションを選択してアニメーションを開始します。 アニメーションを停止するには、 **[テストの停止]** をクリックします。

7. デザイン ビューで **[Form1]** を開きます。

8. フォームに<xref:System.Windows.Forms.Button> 2 つのコントロールを配置します。 それらに`startButton`と`stopButton`という<xref:System.Windows.Forms.Control.Text%2A>名前を設定し、プロパティ値をそれぞれ**Start**および**Stop**に変更します。

9. <xref:System.Windows.Forms.Control.Click> 両方<xref:System.Windows.Forms.Button>のコントロールにイベントハンドラーを実装します。

10. **ツールボックス**で、 **[MarqueeControlTest Components]** タブを開きます。選択できるが`DemoMarqueeControl`表示されます。

11. の`DemoMarqueeControl`インスタンスを**Form1**デザインサーフェイスにドラッグします。

12. イベントハンドラーで、で`Start` メソッドと`Stop`メソッドを呼び出します。`DemoMarqueeControl` <xref:System.Windows.Forms.Control.Click>

```vb
Private Sub startButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Start()
End Sub 'startButton_Click

Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
Me.demoMarqueeControl1.Stop()
End Sub 'stopButton_Click
```

```csharp
private void startButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Start();
}

private void stopButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Stop();
}
```

1. `MarqueeControlTest`プロジェクトをスタートアッププロジェクトとして設定し、実行します。 というフォーム`DemoMarqueeControl`が表示されます。 アニメーションを開始するには、 **[開始]** ボタンをクリックします。 テキストが点滅し、ライトが境界内を移動していることを確認します。

## <a name="next-steps"></a>次の手順

は`MarqueeControlLibrary` 、カスタムコントロールおよび関連するデザイナーの単純な実装を示しています。 このサンプルは、いくつかの方法でより高度なものにすることができます。

- デザイナー `DemoMarqueeControl`でのプロパティの値を変更します。 `MarqueBorder`コントロールを追加し、親インスタンス内にドッキングして、入れ子になった効果を作成します。 `UpdatePeriod`と light 関連のプロパティについて、さまざまな設定を試してみてください。

- の独自の`IMarqueeWidget`実装を作成します。 たとえば、点滅する "ネオンサイン" や、複数のイメージを使用したアニメーション化された記号を作成することができます。

- デザイン時のエクスペリエンスをさらにカスタマイズします。 <xref:System.Windows.Forms.Control.Enabled%2A> と<xref:System.Windows.Forms.Control.Visible%2A>より多くのプロパティをシャドウすることもできます。また、新しいプロパティを追加することもできます。 新しいデザイナー動詞を追加して、子コントロールのドッキングなどの一般的なタスクを簡略化します。

- を`MarqueeControl`ライセンスします。 詳細については、「[方法 :ライセンスコンポーネントとコントロール](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))。

- コントロールのシリアル化方法とコードの生成方法を制御します。 詳細については、「[動的なソースコードの生成とコンパイル](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- [方法: デザイン時機能を利用する Windows フォームコントロールを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
- [デザイン時サポートの拡張](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [カスタムデザイナー](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))

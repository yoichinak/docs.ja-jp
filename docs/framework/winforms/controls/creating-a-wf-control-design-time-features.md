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
ms.openlocfilehash: 4d741beffa5649d1d1593ba3dbb7a1918b669b80
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882310"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成

関連するカスタム デザイナーを作成することにより、カスタム コントロールのデザイン時エクスペリエンスを拡張できます。

このチュートリアルでは、カスタム コントロールのカスタム デザイナーを作成する方法について説明します。 実装、`MarqueeControl`型およびと呼ばれる、関連付けられているデザイナー クラス`MarqueeControlRootDesigner`します。

`MarqueeControl`アニメーションと点滅しているテキストのシアター マーキーのような表示を実装する型。

このコントロールのデザイナーは、カスタムのデザイン時エクスペリエンスを提供するデザイン環境と対話します。 カスタムのデザイナーを使用したカスタムをアセンブルできます`MarqueeControl`アニメーションと多くの組み合わせで点滅しているテキストの実装。 アセンブルされたコントロールは、他の Windows フォーム コントロールのような形式を使用することができます。

このチュートリアルでは、以下のタスクを行います。

- プロジェクトの作成

- コントロール ライブラリ プロジェクトを作成します。

- カスタム コントロール プロジェクトを参照します。

- カスタム コントロールとそのカスタム デザイナーを定義します。

- カスタム コントロールのインスタンスを作成します。

- デザイン時のデバッグ プロジェクトの設定

- カスタム コントロールを実装します。

- カスタム コントロールの子コントロールを作成します。

- MarqueeBorder 子コントロールを作成します。

- シャドウとフィルターのプロパティにカスタム デザイナーを作成します。

- コンポーネントの変更の処理

- デザイナー動詞をカスタム デザイナーに追加します。

- カスタムの UITypeEditor を作成します。

- デザイナーでカスタム コントロールのテスト

完了したら、カスタム コントロールは、次のようになります。

![テキストと開始、停止ボタンを示す範囲を表示するアプリです。](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

完全なコード一覧は、次を参照してください。[方法。デザイン時機能を活用した Windows フォーム コントロールを作成](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))です。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するのには、Visual Studio を必要があります。

## <a name="creating-the-project"></a>プロジェクトの作成

最初の手順では、アプリケーション プロジェクトを作成します。 このプロジェクトを使用すると、カスタム コントロールをホストするアプリケーションをビルドします。

Visual Studio を開き、「ため」と呼ばれる Windows フォーム アプリケーション プロジェクトを作成する (**ファイル** > **新規** > **プロジェクト** > **Visual C#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォーム アプリケーション**).

## <a name="creating-a-control-library-project"></a>コントロール ライブラリ プロジェクトを作成します。

次の手順では、コントロール ライブラリ プロジェクトを作成します。 新しいカスタム コントロールとその対応するカスタム デザイナーを作成します。

### <a name="to-create-the-control-library-project"></a>コントロール ライブラリ プロジェクトを作成するには

1. Windows フォーム コントロール ライブラリ プロジェクトをソリューションに追加します。 「に」プロジェクトを名前します。

2. 使用して**ソリューション エクスプ ローラー**、選択した言語に応じて"UserControl1.cs"または「[usercontrol1.vb]」をという名前のソース ファイルを削除することによって、プロジェクトの既定のコントロールを削除します。 詳細については、「[方法 :削除、削除、および項目を除外](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))します。

3. 新しい追加<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"MarqueeControl"の基本の名前を付けます

4. 使用して**ソリューション エクスプ ローラー**で新しいフォルダーを作成、`MarqueeControlLibrary`プロジェクト。 詳細については、「[方法 :新しいプロジェクト項目の追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))します。 新しいフォルダーの名前を「設計します」

5. 右クリックし、**デザイン**フォルダーと新しいクラスを追加します。 ソース ファイルの「ここで」基本の名前を付けます

6. System.Design アセンブリから型を使用して、そのためにこの参照を追加する必要があります、`MarqueeControlLibrary`プロジェクト。

    > [!NOTE]
    > System.Design アセンブリを使用するには、プロジェクトの .NET Framework、.NET Framework クライアント プロファイルではなく完全なバージョンを対象にする必要があります。 ターゲット フレームワークを変更するを参照してください。[方法.NET Framework のターゲット バージョンを指定する](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)」を参照してください。

## <a name="referencing-the-custom-control-project"></a>カスタム コントロール プロジェクトを参照します。

使用する、`MarqueeControlTest`カスタム コントロールをテストするプロジェクト。 プロジェクト参照を追加するときに、テスト プロジェクトにカスタム コントロールを認識なります、`MarqueeControlLibrary`アセンブリ。

### <a name="to-reference-the-custom-control-project"></a>カスタム コントロール プロジェクトを参照するには

- `MarqueeControlTest`プロジェクトで、プロジェクト参照を追加、`MarqueeControlLibrary`アセンブリ。 使用してください、**プロジェクト** タブで、**参照の追加** ダイアログ ボックスを参照するのではなく、`MarqueeControlLibrary`直接アセンブリ。

## <a name="defining-a-custom-control-and-its-custom-designer"></a>カスタム コントロールとそのカスタム デザイナーを定義します。
 派生して、カスタム コントロール、<xref:System.Windows.Forms.UserControl>クラス。 これにより、コントロール、その他のコントロールを格納して、コントロールの既定の機能を提供します。

 カスタム コントロールは、関連するカスタム デザイナー必要があります。 これにより、カスタム コントロールに特化した独自のデザイン エクスペリエンスを作成することができます。

 使用して、デザイナーでコントロールに関連付ける、<xref:System.ComponentModel.DesignerAttribute>クラス。 カスタム デザイナーの実装は、カスタム コントロールの全体のデザイン時の動作を開発しているため、<xref:System.ComponentModel.Design.IRootDesigner>インターフェイス。

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>カスタム コントロールとそのカスタム デザイナーを定義するには

1. 開く、`MarqueeControl`内のソース ファイル、**コード エディター**します。 ファイルの上部にある次の名前空間をインポートします。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. 追加、<xref:System.ComponentModel.DesignerAttribute>を`MarqueeControl`クラスの宣言。 これには、そのデザイナーを使用したカスタム コントロールが関連付けられます。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. 開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**します。 ファイルの上部にある次の名前空間をインポートします。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. 宣言を変更する`MarqueeControlRootDesigner`から継承するように、<xref:System.Windows.Forms.Design.DocumentDesigner>クラス。 適用、<xref:System.ComponentModel.ToolboxItemFilterAttribute>デザイナーとの対話を指定する、**ツールボックス**します。

     **注**の定義、 `MarqueeControlRootDesigner` "MarqueeControlLibrary.Design"と呼ばれる名前空間のクラスが囲まれています。 この宣言は配置特別な名前空間でのデザイナーをデザインに関連する型用に予約します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. コンス トラクターを定義、`MarqueeControlRootDesigner`クラス。 挿入、<xref:System.Diagnostics.Trace.WriteLine%2A>コンス トラクター本体のステートメント。 これは、デバッグのための便利になります。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a>カスタム コントロールのインスタンスを作成します。
 フォーム上にコントロールのインスタンスを配置するカスタム コントロールのデザイン時動作を観察する`MarqueeControlTest`プロジェクト。

### <a name="to-create-an-instance-of-your-custom-control"></a>カスタム コントロールのインスタンスを作成するには

1. 新しい追加<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlTest`プロジェクト。 新しいソース ファイル「により」の基本の名前を付けます

2. 開く、`DemoMarqueeControl`ファイル、**コード エディター**します。 インポート ファイルの上部にある、`MarqueeControlLibrary`名前空間。

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. 宣言を変更する`DemoMarqueeControl`から継承するように、`MarqueeControl`クラス。

2. プロジェクトをビルドします。

3. Windows フォーム デザイナーで `Form1` を開きます。

4. 検索、**ためコンポーネント** タブで、**ツールボックス**を開きます。 ドラッグ、`DemoMarqueeControl`から、**ツールボックス**フォームにします。

5. プロジェクトをビルドします。

## <a name="setting-up-the-project-for-design-time-debugging"></a>デザイン時のデバッグ プロジェクトの設定

カスタム デザイン時エクスペリエンスを開発しているときに、コントロールとコンポーネントをデバッグする必要があります。 デザイン時にデバッグを許可するプロジェクトを設定する簡単な方法があります。 詳細については、「[チュートリアル:デザイン時にフォーム コントロールのカスタムの Windows をデバッグ](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)します。

### <a name="to-set-up-the-project-for-design-time-debugging"></a>デザイン時のデバッグ プロジェクトを設定するには

1. 右クリックし、`MarqueeControlLibrary`順に選択して**プロパティ**します。

2. "にプロパティ ページ ダイアログ ボックスで選択、**デバッグ**ページ。

3. **開始動作**セクションで、**外部プログラムの開始**します。 できますので、省略記号をクリックして、Visual Studio の別のインスタンスをデバッグ (![. Visual Studio の [プロパティ] ウィンドウで、省略記号ボタン (…)](./media/visual-studio-ellipsis-button.png))、Visual Studio IDE を参照するボタンをクリックします。 実行可能ファイルの名前は、devenv.exe と既定の場所にインストールされている場合は、%programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe がそのパスです。

4. ダイアログ ボックスを閉じるには、[ok] をクリックします。

5. 右クリックし、`MarqueeControlLibrary`プロジェクトし、「設定スタートアップ プロジェクトに」このデバッグ構成を有効にします。

## <a name="checkpoint"></a>チェックポイント

カスタム コントロールのデザイン時の動作をデバッグする準備が整いました。 デバッグ環境が正しく設定されているを確認したら、カスタム コントロールとカスタム デザイナー間の関連付けをテストします。

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>デバッグ環境とデザイナーの関連付けをテストするには

1. 開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**にブレークポイントを配置し、<xref:System.Diagnostics.Trace.WriteLine%2A>ステートメント。

2. F5 キーを押して、デバッグ セッションを開始します。 Visual Studio の新しいインスタンスが作成されたことに注意してください。

3. Visual Studio の新しいインスタンスでは、「ため」ソリューションを開きます。 選択して、ソリューションを簡単に見つけることができます**最近使ったプロジェクト**から、**ファイル**メニュー。 "MarqueeControlTest.sln"ソリューション ファイルは、最近使用したファイルとして表示されます。

4. 開く、`DemoMarqueeControl`デザイナー。 Visual Studio のデバッグ インスタンスがフォーカスを取得し、ブレークポイントで実行を停止することに注意してください。 F5 キーを押して、デバッグ セッションを続行します。

この時点では、すべてが、カスタム コントロールおよびそれに関連付けられているカスタム デザイナーを開発、デバッグするためにします。 このチュートリアルの残りの部分は、コントロールと、デザイナーの機能の実装の詳細に集中します。

## <a name="implementing-your-custom-control"></a>カスタム コントロールを実装します。

`MarqueeControl`は、<xref:System.Windows.Forms.UserControl>少しカスタマイズします。 2 つのメソッドを公開します: `Start`、マーキーのアニメーションを開始して`Stop`アニメーションが停止します。 `MarqueeControl`を実装する子コントロールが含まれています、`IMarqueeWidget`インターフェイス、`Start`と`Stop`各子コントロールと呼び出しを列挙、`StartMarquee`と`StopMarquee`メソッドでは、それぞれ、各子コントロール上実装する`IMarqueeWidget`します。

外観、`MarqueeBorder`と`MarqueeText`コントロールは、レイアウトに依存ように`MarqueeControl`よりも優先されます、<xref:System.Windows.Forms.Control.OnLayout%2A>メソッドと呼び出し<xref:System.Windows.Forms.Control.PerformLayout%2A>でこの型の子コントロール。

これは、程度、`MarqueeControl`カスタマイズします。 ランタイムの機能を実装して、`MarqueeBorder`と`MarqueeText`コントロール、およびデザイン時機能がによって実装される、`MarqueeBorderDesigner`と`MarqueeControlRootDesigner`クラス。

### <a name="to-implement-your-custom-control"></a>カスタム コントロールを実装するには

1. 開く、`MarqueeControl`内のソース ファイル、**コード エディター**します。 実装、`Start`と`Stop`メソッド。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <xref:System.Windows.Forms.Control.OnLayout%2A> メソッドをオーバーライドします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a>カスタム コントロールの子コントロールを作成します。

`MarqueeControl` 2 種類の子コントロールをホストする:`MarqueeBorder`コントロールと`MarqueeText`コントロール。

- `MarqueeBorder`:このコントロールは、「ライト」周囲の境界線を描画します。 ライトは、境界線を移動するように表示されるように、シーケンスで点滅します。 ライトが点滅する速度がという名前のプロパティによって制御される`UpdatePeriod`します。 その他のいくつかのカスタム プロパティは、他のコントロールの外観を決定します。 2 つのメソッドと呼ばれる`StartMarquee`と`StopMarquee`アニメーションが開始し、停止を制御します。

- `MarqueeText`:このコントロールは、点滅している文字列を描画します。 ように、`MarqueeBorder`コントロール、テキストが点滅速度はによって制御される、`UpdatePeriod`プロパティ。 `MarqueeText`コントロールもあります、`StartMarquee`と`StopMarquee`で共通のメソッド、`MarqueeBorder`コントロール。

デザイン時に、`MarqueeControlRootDesigner`これら 2 つの制御の型に追加することができます、`MarqueeControl`の任意の組み合わせ。

2 つのコントロールの一般的な機能を考慮にというインターフェイス`IMarqueeWidget`します。 これにより、`MarqueeControl`を範囲に関連する子コントロールを検出し、特別な処理を付与します。

定期的なアニメーション機能を実装するには、使用<xref:System.ComponentModel.BackgroundWorker>オブジェクトから、<xref:System.ComponentModel?displayProperty=nameWithType>名前空間。 使って<xref:System.Windows.Forms.Timer>オブジェクトが多く`IMarqueeWidget`オブジェクトが存在する、1 つの UI スレッドが、アニメーションを進めることができません。

### <a name="to-create-a-child-control-for-your-custom-control"></a>カスタム コントロールの子コントロールを作成するには

1. クラスの新しいアイテムを追加、`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"IMarqueeWidget"の基本の名前を付けます

2. 開く、`IMarqueeWidget`内のソース ファイル、**コード エディター**から宣言を変更して`class`に`interface`:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. 次のコードを追加、 `IMarqueeWidget` 2 つの方法と、マーキー アニメーションを操作するプロパティを公開するインターフェイス。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. 新しい追加**カスタム コントロール**項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル「ただし」の基本の名前を付けます

5. ドラッグ、<xref:System.ComponentModel.BackgroundWorker>コンポーネントから、**ツールボックス**上に、`MarqueeText`コントロール。 このコンポーネントを許可するが、`MarqueeText`自体を非同期的に更新するコントロール。

6. [プロパティ] ウィンドウで次のように設定します。、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgress`と<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティ`true`します。 これらの設定により、<xref:System.ComponentModel.BackgroundWorker>定期的に発生させるコンポーネント、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントと非同期更新をキャンセルします。 詳細については、次を参照してください。 [BackgroundWorker コンポーネント](backgroundworker-component.md)します。

7. 開く、`MarqueeText`内のソース ファイル、**コード エディター**します。 ファイルの上部にある次の名前空間をインポートします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. 宣言を変更する`MarqueeText`から継承する<xref:System.Windows.Forms.Label>を実装して、`IMarqueeWidget`インターフェイス。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. 公開したプロパティに対応するインスタンス変数を宣言し、それらをコンス トラクターで初期化します。 `isLit`フィールドかどうかをテキストで指定された色で描画する、`LightColor`プロパティ。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. `IMarqueeWidget` インターフェイスを実装します。

    `StartMarquee`と`StopMarquee`メソッドを呼び出す、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>と<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>開始およびアニメーションを停止するメソッド。

    <xref:System.ComponentModel.CategoryAttribute.Category%2A>と<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>属性に適用されます、 `UpdatePeriod` 「マーキー」と呼ばれる [プロパティ] ウィンドウのカスタム セクションに表示されるプロパティ。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. プロパティ アクセサーを実装します。 クライアントに 2 つのプロパティを公開:`LightColor`と`DarkColor`します。 <xref:System.ComponentModel.CategoryAttribute.Category%2A>と<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>属性はこれらのプロパティに適用されるため、「マーキー。」と呼ばれる [プロパティ] ウィンドウのカスタムのセクションでプロパティが表示されます。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. ハンドラーを実装、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。

    <xref:System.ComponentModel.BackgroundWorker.DoWork>によって指定されたミリ秒数のイベント ハンドラーがスリープ状態`UpdatePeriod`が発生し、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント、コードが呼び出すことによって、アニメーションを停止するまで<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>します。

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラーは、テキストの点滅の外観を与える、明暗の状態を切り替えます。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. 上書き、<xref:System.Windows.Forms.Control.OnPaint%2A>アニメーションを有効にするメソッド。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. F6 キーを押してソリューションをビルドします。

## <a name="create-the-marqueeborder-child-control"></a>MarqueeBorder 子コントロールを作成します。

`MarqueeBorder`コントロールがやや高度な`MarqueeText`コントロール。 その他のプロパティと、アニメーションがある、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、複雑です。 原則として、これとよく似ていますが、`MarqueeText`コントロール。

`MarqueeBorder`コントロールで子コントロールを持つことができます、注意する必要がある<xref:System.Windows.Forms.Control.Layout>イベント。

### <a name="to-create-the-marqueeborder-control"></a>MarqueeBorder コントロールを作成するには

1. 新しい追加**カスタム コントロール**項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"MarqueeBorder"の基本の名前を付けます

2. ドラッグ、<xref:System.ComponentModel.BackgroundWorker>コンポーネントから、**ツールボックス**上に、`MarqueeBorder`コントロール。 このコンポーネントを許可するが、`MarqueeBorder`自体を非同期的に更新するコントロール。

3. [プロパティ] ウィンドウで次のように設定します。、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgress`と<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティ`true`します。 これらの設定により、<xref:System.ComponentModel.BackgroundWorker>定期的に発生させるコンポーネント、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントと非同期更新をキャンセルします。 詳細については、次を参照してください。 [BackgroundWorker コンポーネント](backgroundworker-component.md)します。

4. [プロパティ] ウィンドウで、イベント ボタンをクリックします。 ハンドラーのアタッチ、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。

5. 開く、`MarqueeBorder`内のソース ファイル、**コード エディター**します。 ファイルの上部にある次の名前空間をインポートします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. 宣言を変更する`MarqueeBorder`から継承する<xref:System.Windows.Forms.Panel>を実装して、`IMarqueeWidget`インターフェイス。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. 管理するための 2 つの列挙型を宣言、`MarqueeBorder`コントロールの状態:`MarqueeSpinDirection`をライト「回転」境界線の方向を決定して`MarqueeLightShape`、(正方形または循環) のライトの形状を決定します。 配置する前にこれらの宣言、`MarqueeBorder`クラスの宣言。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. 公開したプロパティに対応するインスタンス変数を宣言し、それらをコンス トラクターで初期化します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. `IMarqueeWidget` インターフェイスを実装します。

    `StartMarquee`と`StopMarquee`メソッドを呼び出す、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>と<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>開始およびアニメーションを停止するメソッド。

    `MarqueeBorder`コントロールで子コントロールを含めることができます、`StartMarquee`メソッドは、すべての子コントロールと呼び出しを列挙します。`StartMarquee`を実装するもので`IMarqueeWidget`します。 `StopMarquee`メソッドのような実装があります。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. プロパティ アクセサーを実装します。 `MarqueeBorder`コントロールの外観を制御するためのいくつかのプロパティがあります。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. ハンドラーを実装、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。

    <xref:System.ComponentModel.BackgroundWorker.DoWork>によって指定されたミリ秒数のイベント ハンドラーがスリープ状態`UpdatePeriod`が発生し、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント、コードが呼び出すことによって、アニメーションを停止するまで<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>します。

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラーは、元となる、他のライトの/暗状態を判断は、"base"光と呼び出しの位置をインクリメント、<xref:System.Windows.Forms.Control.Refresh%2A>メソッドを呼び出すと、コントロール自体を再描画します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. ヘルパー メソッドを実装`IsLit`と`DrawLight`します。

    `IsLit`メソッドは、指定された位置にライトの色を決定します。 指定された色では「点灯」ライトが描画される、`LightColor`プロパティ、および [ダーク] にあるものがで指定された色で描画される、`DarkColor`プロパティ。

    `DrawLight`メソッドが適切な色、形状、および位置を使用して、ライトを描画します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. 上書き、<xref:System.Windows.Forms.Control.OnLayout%2A>と<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。

    <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、ライトの端を描画、`MarqueeBorder`コントロール。

    <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの大きさによって異なります、`MarqueeBorder`コントロール、レイアウトが変更されるたびに呼び出す必要があります。 これを実現するにはオーバーライド<xref:System.Windows.Forms.Control.OnLayout%2A>を呼び出すと<xref:System.Windows.Forms.Control.Refresh%2A>します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>シャドウとフィルターのプロパティにカスタム デザイナーを作成します。

`MarqueeControlRootDesigner`クラスがルート デザイナーの実装を提供します。 動作するだけでなく、このデザイナー、 `MarqueeControl`、カスタム デザイナーに具体的には関連付けられている必要があります、`MarqueeBorder`コントロール。 このデザイナーは、カスタム ルート デザイナーのコンテキストで適切なカスタム動作を提供します。

具体的には、 `MarqueeBorderDesigner` 「シャドウ」され、特定のプロパティをフィルター処理、`MarqueeBorder`コントロール、デザイン環境との相互作用を変更します。

コンポーネントのプロパティ アクセサーの呼び出しを受け取ることは「シャドウ」と呼ばれます デザイナーによって、ユーザーによって設定された値を追跡し、必要に応じてその値をデザインするコンポーネントに渡します。

この例で、<xref:System.Windows.Forms.Control.Visible%2A>と<xref:System.Windows.Forms.Control.Enabled%2A>でプロパティをシャドウは、`MarqueeBorderDesigner`からユーザーを防ぐことが、`MarqueeBorder`コントロールを非表示またはデザイン時に無効になっています。

デザイナーを追加およびプロパティを削除することもできます。 この例で、 <xref:System.Windows.Forms.Control.Padding%2A> 、デザイン時にプロパティを削除は、`MarqueeBorder`コントロールで指定されたライトのサイズに基づいての余白をプログラムで設定する、`LightSize`プロパティ。

基本クラス`MarqueeBorderDesigner`は<xref:System.ComponentModel.Design.ComponentDesigner>属性、プロパティ、およびデザイン時にコントロールによって公開されるイベントを変更するメソッドを持ちます。

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

これらのメソッドを使用して、コンポーネントのパブリック インターフェイスを変更する場合は、これらの規則に従う必要があります。

- 項目の追加または削除、`PreFilter`メソッドのみ

- 既存の項目を変更、`PostFilter`メソッドのみ

- 常に最初に呼び出す基本の実装、`PreFilter`メソッド

- 基本実装を最終呼び出す常に、`PostFilter`メソッド

これらの規則に従うことにより、すべてのデザイナー、デザイン時環境であるように設計されているすべてのコンポーネントの一貫性のあるビュー。

<xref:System.ComponentModel.Design.ComponentDesigner>クラスの特定のインスタンス変数を作成する必要があるが、影付きのプロパティの値を管理するためのディクショナリを提供します。

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>シャドウとフィルターのプロパティをカスタム デザイナーを作成するには

1. 右クリックし、**デザイン**フォルダーと新しいクラスを追加します。 ソース ファイル"MarqueeBorderDesigner"の基本の名前を付けます

2. 開く、`MarqueeBorderDesigner`内のソース ファイル、**コード エディター**します。 ファイルの上部にある次の名前空間をインポートします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. 宣言を変更する`MarqueeBorderDesigner`から継承する<xref:System.Windows.Forms.Design.ParentControlDesigner>します。

    `MarqueeBorder`コントロールで子コントロールを含めることができます`MarqueeBorderDesigner`から継承<xref:System.Windows.Forms.Design.ParentControlDesigner>親子の対話を処理します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. 基本実装をオーバーライド<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. 
  <xref:System.Windows.Forms.Control.Enabled%2A> プロパティと <xref:System.Windows.Forms.Control.Visible%2A> プロパティを実装します。 これらの実装では、コントロールのプロパティをシャドウします。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a>コンポーネントの変更の処理
 `MarqueeControlRootDesigner`クラスのカスタム デザイン時エクスペリエンスを提供する、`MarqueeControl`インスタンス。 デザイン時の機能のほとんどが継承、<xref:System.Windows.Forms.Design.DocumentDesigner>クラスは 2 つの特定のカスタマイズを実装するコードを: コンポーネントの変更の処理とデザイナー動詞を追加します。

 ユーザー設計として、 `MarqueeControl` 、インスタンスのルート デザイナーに変更の追跡は、`MarqueeControl`とその子コントロール。 便利なサービス、デザイン時環境では<xref:System.ComponentModel.Design.IComponentChangeService>コンポーネントの状態に変更を追跡します。

 使用環境を照会することによってこのサービスへの参照を取得する、<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>メソッド。 クエリが成功した場合、デザイナーがのハンドラーをアタッチできます、<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>イベントと、デザイン時に一貫性のある状態を維持するために必要なタスクを実行します。

 場合、`MarqueeControlRootDesigner`呼び出しは、クラス、<xref:System.Windows.Forms.Control.Refresh%2A>各`IMarqueeWidget`オブジェクトに含まれる、`MarqueeControl`します。 これにより、`IMarqueeWidget`オブジェクトにプロパティがその親のようなときに適切に再描画<xref:System.Windows.Forms.Control.Size%2A>変更されます。

### <a name="to-handle-component-changes"></a>コンポーネントの変更を処理するには

1. 開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**をオーバーライドし、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>メソッド。 基本実装を呼び出す<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>に対してクエリを実行し、<xref:System.ComponentModel.Design.IComponentChangeService>します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. 実装、<xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>イベント ハンドラー。 送信側のコンポーネントの種類、テストの場合、 `IMarqueeWidget`、呼び出すその<xref:System.Windows.Forms.Control.Refresh%2A>メソッド。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a>デザイナー動詞をカスタム デザイナーに追加します。

デザイナー動詞は、イベント ハンドラーにリンクされているメニュー コマンドです。 デザイナー動詞は、デザイン時コンポーネントのショートカット メニューに追加されます。 詳細については、「 <xref:System.ComponentModel.Design.DesignerVerb> 」を参照してください。

2 つのデザイナー動詞は、デザイナーに追加されます。**テスト実行**と**テストを停止**します。 これらの動詞の実行時の動作を表示することにより、`MarqueeControl`デザイン時にします。 これらの動詞に追加されます、`MarqueeControlRootDesigner`します。

ときに**テストの実行**が呼び出されると、動詞のイベント ハンドラーが呼び出されます、`StartMarquee`メソッドを`MarqueeControl`します。 ときに**テストの停止**が呼び出されると、動詞のイベント ハンドラーが呼び出されます、`StopMarquee`メソッドを`MarqueeControl`します。 実装、`StartMarquee`と`StopMarquee`メソッドが格納されているコントロールを実装するのにこれらのメソッドを呼び出す`IMarqueeWidget`、すべて含まれている`IMarqueeWidget`コントロールがテストに参加することもできます。

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>デザイナー動詞をカスタム デザイナーに追加するには

1. `MarqueeControlRootDesigner`クラスでという名前のイベント ハンドラーを追加`OnVerbRunTest`と`OnVerbStopTest`します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. これらのイベント ハンドラーを対応するデザイナー動詞に接続します。 `MarqueeControlRootDesigner` 継承、<xref:System.ComponentModel.Design.DesignerVerbCollection>その基本クラスから。 2 つ作成する新しい<xref:System.ComponentModel.Design.DesignerVerb>オブジェクトし、では、このコレクションに追加、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>メソッド。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a>カスタムの UITypeEditor を作成します。

ユーザーのカスタム デザイン時エクスペリエンスを作成するときに、[プロパティ] ウィンドウでカスタム操作を作成することが望ましいは多くの場合。 これを実現するには作成を<xref:System.Drawing.Design.UITypeEditor>します。 詳細については、「[方法 :UI 型エディターを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120))します。

`MarqueeBorder`コントロールのプロパティ ウィンドウでいくつかのプロパティを公開します。 これらのプロパティの 2 つ`MarqueeSpinDirection`と`MarqueeLightShape`列挙体によって表されます。 UI 型エディターでは、使用方法を示す、`MarqueeLightShape`プロパティが関連付けられている必要があります<xref:System.Drawing.Design.UITypeEditor>クラス。

### <a name="to-create-a-custom-ui-type-editor"></a>カスタム UI 型エディターを作成するには

1. 開く、`MarqueeBorder`内のソース ファイル、**コード エディター**します。

2. 定義で、`MarqueeBorder`クラスと呼ばれるクラスを宣言`LightShapeEditor`から派生した<xref:System.Drawing.Design.UITypeEditor>します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. 宣言、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>というインスタンス変数`editorService`します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> メソッドをオーバーライドします。 この実装を返します<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>、デザイン環境を表示する方法について説明する、`LightShapeEditor`します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> メソッドをオーバーライドします。 この実装はクエリのデザイン環境、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>オブジェクト。 成功すると、作成、`LightShapeSelectionControl`します。 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>を開始するメソッドが呼び出される、`LightShapeEditor`します。 この呼び出しからの戻り値は、デザイン環境に返されます。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>カスタム ビュー コントロールを作成します。

1. `MarqueeLightShape`プロパティには、2 つの種類のライトの図形がサポートしています:`Square`と`Circle`します。 [プロパティ] ウィンドウで、これらの値をグラフィカルに表示するためだけに使用するカスタム コントロールを作成します。 このカスタム コントロールで使用される、<xref:System.Drawing.Design.UITypeEditor>プロパティ ウィンドウと対話します。

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>カスタム UI 型エディターのビュー コントロールを作成するには

1. 新しい追加<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"LightShapeSelectionControl"の基本の名前を付けます

2. 2 つをドラッグして<xref:System.Windows.Forms.Panel>コントロールを**ツールボックス**上に、`LightShapeSelectionControl`します。 名前を付けます`squarePanel`と`circlePanel`します。 サイド バイ サイドそれらを配置します。 設定、<xref:System.Windows.Forms.Control.Size%2A>両方のプロパティ<xref:System.Windows.Forms.Panel>にコントロールを (60, 60)。 設定、<xref:System.Windows.Forms.Control.Location%2A>のプロパティ、`squarePanel`への制御 (8, 10)。 設定、<xref:System.Windows.Forms.Control.Location%2A>のプロパティ、`circlePanel`への制御 (80, 10)。 最後に、設定、<xref:System.Windows.Forms.Control.Size%2A>のプロパティ、`LightShapeSelectionControl`に (150, 80)。

3. 開く、`LightShapeSelectionControl`内のソース ファイル、**コード エディター**します。 インポート ファイルの上部にある、<xref:System.Windows.Forms.Design?displayProperty=nameWithType>名前空間。

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. 実装<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、`squarePanel`と`circlePanel`コントロール。 これらのメソッドを呼び出す<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>カスタムを終了する<xref:System.Drawing.Design.UITypeEditor>セッションを編集します。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. 宣言、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>というインスタンス変数`editorService`します。

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. 宣言を`MarqueeLightShape`というインスタンス変数`lightShapeValue`します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. `LightShapeSelectionControl`コンス トラクター、アタッチ、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを`squarePanel`と`circlePanel`コントロールの<xref:System.Windows.Forms.Control.Click>イベント。 割り当てるコンス トラクター オーバー ロードを定義することも、`MarqueeLightShape`値には、デザイン環境から、`lightShapeValue`フィールド。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. <xref:System.ComponentModel.Component.Dispose%2A>メソッド、デタッチ、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。 LightShapeSelectionControl.Designer.cs または LightShapeSelectionControl.Designer.vb ファイルを開きの既定の定義を削除、<xref:System.ComponentModel.Component.Dispose%2A>メソッド。

5. 
  `LightShape` プロパティを実装します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。 この実装は、塗りつぶされた四角形と円を描画します。 また、どちらか 1 つの図形の周りに罫線を描画することで、選択した値を強調表示します。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a>デザイナーでカスタム コントロールのテスト

この時点では、ビルドすることができます、`MarqueeControlLibrary`プロジェクト。 継承するコントロールを作成して、実装をテスト、`MarqueeControl`クラスおよびフォーム上で使用します。

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>カスタムを作成するには

1. Windows フォーム デザイナーで `DemoMarqueeControl` を開きます。 このインスタンスを作成、`DemoMarqueeControl`を入力し、インスタンス内の表示、`MarqueeControlRootDesigner`型。

2. **ツールボックス**、オープン、**にコンポーネント**タブ。表示されます、`MarqueeBorder`と`MarqueeText`コントロールを選択できます。

3. インスタンスをドラッグして、`MarqueeBorder`コントロールを`DemoMarqueeControl`デザイン サーフェイス。 このドッキング`MarqueeBorder`コントロールを親コントロール。

4. インスタンスをドラッグして、`MarqueeText`コントロールを`DemoMarqueeControl`デザイン サーフェイス。

5. ソリューションをビルドします。

6. 右クリックし、`DemoMarqueeControl`ショートカット メニューを選択し、**テストの実行**アニメーションを開始するにはオプションです。 クリックして**テストの停止**アニメーションを停止します。

7. デザイン ビューで **[Form1]** を開きます。

8. 2 つ配置<xref:System.Windows.Forms.Button>フォーム上のコントロール。 という名前を付けます`startButton`と`stopButton`、変更して、<xref:System.Windows.Forms.Control.Text%2A>プロパティ値を**開始**と**停止**、それぞれします。

9. 実装<xref:System.Windows.Forms.Control.Click>両方のイベント ハンドラー<xref:System.Windows.Forms.Button>コントロール。

10. **ツールボックス**、オープン、**ためコンポーネント**タブ。表示されます、`DemoMarqueeControl`選択できます。

11. インスタンスをドラッグ`DemoMarqueeControl`上に、 **Form1**デザイン サーフェイス。

12. <xref:System.Windows.Forms.Control.Click> 、イベント ハンドラーを呼び出す、`Start`と`Stop`メソッド、`DemoMarqueeControl`します。

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

1. 設定、`MarqueeControlTest`スタートアップ プロジェクトとしてプロジェクトを実行します。 表示するフォームが表示されます、`DemoMarqueeControl`します。 をクリックして、**開始**アニメーションを開始するボタンをクリックします。 テキストが点滅し、ライトの境界線を移動するが表示されます。

## <a name="next-steps"></a>次の手順

`MarqueeControlLibrary`カスタム コントロールと関連付けられているデザイナーの単純な実装を示します。 いくつかの方法で行うと、このサンプルがより高度です。

- プロパティ値を変更、`DemoMarqueeControl`デザイナー。 さらに追加`MarqueBorder`を制御し、入れ子になった効果を作成するには、その親インスタンス内でドッキングします。 別の設定を使用した実験、`UpdatePeriod`と光に関連するプロパティ。

- 独自の実装を作成する`IMarqueeWidget`します。 など、複数のイメージで、点滅「neon サインイン」またはアニメーションの記号を作成できます。

- さらに、デザイン時のエクスペリエンスをカスタマイズします。 多くのプロパティをシャドウ試して<xref:System.Windows.Forms.Control.Enabled%2A>と<xref:System.Windows.Forms.Control.Visible%2A>、し、新しいプロパティを追加できます。 子コントロールのドッキングなどの一般的なタスクを簡略化の新しいデザイナー動詞を追加します。

- ライセンス、`MarqueeControl`します。 詳細については、「[方法 :コンポーネントとコントロールのライセンスの](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))します。

- コントロールがシリアル化する方法とそれらのコードを生成する方法を制御します。 詳細については、次を参照してください。[動的ソース コードの生成とコンパイル](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- [方法: デザイン時機能を活用した Windows フォーム コントロールを作成します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
- [デザイン時サポートの拡張](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [カスタム デザイナー](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))

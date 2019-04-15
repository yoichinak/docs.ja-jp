---
title: Visual Studio で WPF アプリに InkCanvas を作成します。
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 4309b1108b2ea96eb298ff3bb876a0f63b80dc32
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343598"
---
# <a name="get-started-with-ink-in-wpf"></a>WPF のインクを概要します。

Windows Presentation Foundation (WPF) が、インク機能を使用するデジタル インクをアプリに組み込むことで簡単です。

## <a name="prerequisites"></a>必須コンポーネント

次の例を使用するには、最初インストール[Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)します。 基本的な WPF アプリを記述する方法を理解することもできます。 WPF の概要については、次を参照してください。[チュートリアル。初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。

## <a name="quick-start"></a>クイック スタート

このセクションでは、インクを収集する簡単な WPF アプリケーションを作成できます。

### <a name="got-ink"></a>インクを入手されましたか。

WPF アプリを作成するには、インクをサポートしています。

1. Visual Studio を開きます。

2. 新規作成**WPF アプリ**します。

   **新しいプロジェクト**ダイアログ ボックスで、展開、**インストール済み** > **Visual c#** または**Visual Basic**  >  **Windows デスクトップ**カテゴリ。 次に、選択、 **WPF アプリ (.NET Framework)** アプリ テンプレート。 名前を入力し、 **OK**します。

   Visual Studio は、プロジェクトを作成し、 *MainWindow.xaml*デザイナーが開きます。

3. 型`<InkCanvas/>`間、`<Grid>`タグ。

   ![InkCanvas タグを持つ XAML デザイナー](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. キーを押して**F5**デバッガーでアプリケーションを起動します。

5. スタイラス ペンやマウスを使用して、記述**hello world**ウィンドウ。

インクと同等の 12 のキー操作で"hello world"アプリケーションを記述しました。

### <a name="spice-up-your-app"></a>アプリを改良します。

WPF の機能がいくつかの利点を見てみましょう。 開始タグと終了の間ですべてのものを置き換える\<ウィンドウ > 次のマークアップ タグ。

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

この XAML は、手描き入力サーフェイス グラデーション ブラシのバック グラウンドを作成します。

![WPF アプリで画面を手描き入力のグラデーションの色](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>一部の XAML コードを追加します。

XAML を使用する非常に簡単にユーザー インターフェイスをデザイン、現実世界の任意のアプリケーションはイベントを処理するコードを追加する必要があります。 マウスから応答を右クリックして、インクにズーム インする簡単な例を次に示します。

1. 設定、 `MouseRightButtonUp` XAML 内のハンドラー。

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. **ソリューション エクスプ ローラー**MainWindow.xaml を展開し、分離コード ファイル (MainWindow.xaml.cs または MainWindow.xaml.vb) を開きます。 次のイベント ハンドラーのコードを追加します。

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. アプリケーションを実行します。 、手描き入力を追加し、マウスで右クリックまたはプレス アンド ホールドに相当するスタイラスを使用して実行します。

   マウスの右ボタンをクリックするたびに拡大表示されます。

### <a name="use-procedural-code-instead-of-xaml"></a>手続き型コードを使用して、XAML ではなく

手続き型コードからすべての WPF 機能にアクセスできます。 Wpf の XAML をまったく使用しない"こんにちはインク World"アプリケーションを作成する次の手順に従います。

1. Visual Studio で新しいコンソール アプリケーション プロジェクトを作成します。

   **新しいプロジェクト**ダイアログ ボックスで、展開、**インストール済み** > **Visual c#** または**Visual Basic**  >  **Windows デスクトップ**カテゴリ。 次に、選択、**コンソール アプリ (.NET Framework)** アプリ テンプレート。 名前を入力し、 **OK**します。

1. 次のコードを Program.cs または Program.vb ファイルに貼り付けます。

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. 右クリックし、PresentationCore、PresentationFramework、WindowsBase アセンブリへの参照を追加**参照**で**ソリューション エクスプ ローラー**を選択して**参照の追加**.

   ![PresentationCore と PresentationFramework を示す参照マネージャー](./media/getting-started-with-ink/references.png)

1. キーを押してアプリケーションをビルド**F5**します。

## <a name="see-also"></a>関連項目

- [デジタル インク](digital-ink.md)
- [インクの収集](collecting-ink.md)
- [手書き認識](handwriting-recognition.md)
- [インクの格納](storing-ink.md)

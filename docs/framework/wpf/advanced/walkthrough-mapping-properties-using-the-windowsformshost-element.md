---
title: 'チュートリアル: WindowsFormsHost 要素を使用してプロパティのマッピング'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 86a7a8a937b9407690d7f1981b91857d1b44ded1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373882"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>チュートリアル: WindowsFormsHost 要素を使用してプロパティのマッピング

このチュートリアルは、使用する方法を示します、<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>プロパティにマップする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。

このチュートリアルでは、以下のタスクを行います。

-   プロジェクトの作成。

-   アプリケーションのレイアウトを定義します。

-   新しいプロパティ マッピングを定義します。

-   既定のプロパティ マッピングを削除しています。

-   既定のプロパティ マッピングを置換します。

-   既定のプロパティ マッピングを拡張します。

このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。 [WindowsFormsHost 要素のサンプルを使用してプロパティをマッピング](https://go.microsoft.com/fwlink/?LinkID=160019)します。

マップが完了したらができます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

-   Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>作成し、プロジェクトを設定します。

1.  作成、 **WPF アプリ**という名前のプロジェクト`PropertyMappingWithWfhSample`します。

2.  **ソリューション エクスプ ローラー**、WindowsFormsIntegration.dll という WindowsFormsIntegration アセンブリへの参照を追加します。

3.  **ソリューション エクスプ ローラー**System.Drawing、および System.Windows.Forms アセンブリへの参照を追加します。

## <a name="defining-the-application-layout"></a>アプリケーションのレイアウトを定義します。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションで使用する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストに要素を[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。

### <a name="to-define-the-application-layout"></a>アプリケーションのレイアウトを定義するには

1.  Window1.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]します。

2.  既存のコードを次のコードに置き換えます。

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3.  Window1.xaml.cs のコード エディターでを開きます。

4.  ファイルの上部にある次の名前空間をインポートします。

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>新しいプロパティ マッピングを定義します。

<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素はいくつかの既定のプロパティのマッピングを提供します。 新しいプロパティの割り当てを追加するには呼び出すことによって、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。

### <a name="to-define-a-new-property-mapping"></a>新しいプロパティ マッピングを定義するには

-   定義に次のコードをコピー、`Window1`クラス。

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     `AddClipMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.UIElement.Clip%2A>プロパティ。

     `OnClipChange`メソッドは、変換、<xref:System.Windows.UIElement.Clip%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>プロパティ。

     `Window1_SizeChanged`メソッドは処理ウィンドウの<xref:System.Windows.FrameworkElement.SizeChanged>イベントと、アプリケーション ウィンドウに合わせてクリッピング領域のサイズします。

## <a name="removing-a-default-property-mapping"></a>既定のプロパティ マッピングを削除します。

既定のプロパティ マッピングを削除する、<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。

### <a name="to-remove-a-default-property-mapping"></a>既定のプロパティ マッピングを削除するには

-   定義に次のコードをコピー、`Window1`クラス。

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     `RemoveCursorMapping`メソッドの既定のマッピングを削除する、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティ。

## <a name="replacing-a-default-property-mapping"></a>既定のプロパティ マッピングを置き換える

既定のマッピングと呼び出しを削除することで、既定のプロパティ マッピングを置き換える、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。

### <a name="to-replace-a-default-property-mapping"></a>既定のプロパティ マッピングを置換するには

-   定義に次のコードをコピー、`Window1`クラス。

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     `ReplaceFlowDirectionMapping`メソッドの既定のマッピングを置き換える、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティ。

     `OnFlowDirectionChange`メソッドは、変換、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>プロパティ。

     `cb_CheckedChanged`メソッド ハンドル、<xref:System.Windows.Forms.CheckBox.CheckedChanged>上のイベント、<xref:System.Windows.Forms.CheckBox>コントロール。 割り当てます、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティの値に基づいて、<xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティ

## <a name="extending-a-default-property-mapping"></a>既定のプロパティ マッピングの拡張

既定のプロパティ マッピングを使用しても、独自のマッピングでは拡張できます。

### <a name="to-extend-a-default-property-mapping"></a>既定のプロパティ マッピングを拡張するには

-   定義に次のコードをコピー、`Window1`クラス。

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     `ExtendBackgroundMapping`メソッドでは、カスタム プロパティ トランスレーターを追加、既存<xref:System.Windows.Controls.Control.Background%2A>プロパティ マッピングします。

     `OnBackgroundChange`メソッドは、ホストされるコントロールに、特定のイメージを割り当てます<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティ。 `OnBackgroundChange`既定のプロパティ マッピングが適用された後、メソッドが呼び出されます。

## <a name="initializing-your-property-mappings"></a>プロパティ マッピングの初期化

既に説明したメソッドを呼び出すことによって、プロパティのマッピングを設定、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラー。

### <a name="to-initialize-your-property-mappings"></a>プロパティ マッピングを初期化するには

1.  定義に次のコードをコピー、`Window1`クラス。

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     `WindowLoaded`メソッド ハンドル、<xref:System.Windows.FrameworkElement.Loaded>イベントと、次の初期化を実行します。

    -   作成、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox>コントロール。

    -   プロパティ マッピングを設定するチュートリアルの前半で定義されているメソッドを呼び出します。

    -   マップされたプロパティに初期値を割り当てます。

2.  **F5** キーを押してアプリケーションをビルドし、実行します。 効果を確認するチェック ボックスをクリックして、<xref:System.Windows.FrameworkElement.FlowDirection%2A>マッピングします。 チェック ボックスをクリックすると、レイアウトは左から右方向を反転させます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: WPF での Windows フォーム コントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
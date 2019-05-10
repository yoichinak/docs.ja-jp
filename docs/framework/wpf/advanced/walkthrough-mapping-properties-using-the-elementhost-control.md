---
title: 'チュートリアル: ElementHost コントロールを使用したプロパティの割り当て'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 3c74878a91f89e14837b42a45a35ab35bcd5cf68
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650826"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>チュートリアル: ElementHost コントロールを使用したプロパティの割り当て

このチュートリアルは、使用する方法を示します、<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>プロパティにマップする[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素。

このチュートリアルでは、以下のタスクを行います。

- プロジェクトの作成。

- 新しいプロパティ マッピングを定義します。

- 既定のプロパティ マッピングを削除しています。

- 既定のプロパティ マッピングを拡張します。

このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。 [ElementHost コントロールのサンプルを使用してプロパティをマッピング](https://go.microsoft.com/fwlink/?LinkID=160018)します。

マップが完了したらができます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]を対応するプロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストされている要素のプロパティ。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- Visual Studio 2017

## <a name="creating-the-project"></a>プロジェクトの作成

### <a name="to-create-the-project"></a>プロジェクトを作成するには

1. 作成、 **Windows フォーム アプリ**という名前のプロジェクト`PropertyMappingWithElementHost`します。

2. **ソリューション エクスプ ローラー**、次の参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。

    - PresentationCore

    - PresentationFramework

    - WindowsBase

    - WindowsFormsIntegration

3. 先頭に次のコードをコピー、`Form1`コード ファイル。

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Windows フォーム デザイナーで `Form1` を開きます。 イベント ハンドラーを追加するためのフォームをダブルクリックして、<xref:System.Windows.Forms.Form.Load>イベント。

5. Windows フォーム デザイナーに戻るし、フォームのイベント ハンドラーを追加<xref:System.Windows.Forms.Control.Resize>イベント。 詳細については、「[方法 :デザイナーを使用してイベント ハンドラーを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))します。

6. 宣言、<xref:System.Windows.Forms.Integration.ElementHost>フィールドに、`Form1`クラス。

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>新しいプロパティのマッピングを定義します。

<xref:System.Windows.Forms.Integration.ElementHost>コントロールはいくつかの既定のプロパティのマッピングを提供します。 新しいプロパティの割り当てを追加するには呼び出すことによって、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>します。

### <a name="to-define-new-property-mappings"></a>新しいプロパティのマッピングを定義するには

1. 定義に次のコードをコピー、`Form1`クラス。

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     `AddMarginMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.Forms.Control.Margin%2A>プロパティ。

     `OnMarginChange`メソッドは、変換、<xref:System.Windows.Forms.Control.Margin%2A>プロパティを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.FrameworkElement.Margin%2A>プロパティ。

2. 定義に次のコードをコピー、`Form1`クラス。

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     `AddRegionMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.Forms.Control.Region%2A>プロパティ。

     `OnRegionChange`メソッドは、変換、<xref:System.Windows.Forms.Control.Region%2A>プロパティを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.UIElement.Clip%2A>プロパティ。

     `Form1_Resize`メソッドの処理、フォームの<xref:System.Windows.Forms.Control.Resize>イベントと、ホストされている要素に合わせてクリッピング領域のサイズします。

## <a name="removing-a-default-property-mapping"></a>既定のプロパティ マッピングを削除します。

既定のプロパティ マッピングを削除する、<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>します。

### <a name="to-remove-a-default-property-mapping"></a>既定のプロパティ マッピングを削除するには

- 定義に次のコードをコピー、`Form1`クラス。

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     `RemoveCursorMapping`メソッドの既定のマッピングを削除する、<xref:System.Windows.Forms.Control.Cursor%2A>プロパティ。

## <a name="extending-a-default-property-mapping"></a>既定のプロパティ マッピングの拡張

既定のプロパティ マッピングを使用しても、独自のマッピングでは拡張できます。

### <a name="to-extend-a-default-property-mapping"></a>既定のプロパティ マッピングを拡張するには

- 定義に次のコードをコピー、`Form1`クラス。

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     `ExtendBackColorMapping`メソッドでは、カスタム プロパティ トランスレーターを追加、既存<xref:System.Windows.Forms.Control.BackColor%2A>プロパティ マッピングします。

     `OnBackColorChange`メソッドは、ホストされるコントロールに、特定のイメージを割り当てます<xref:System.Windows.Controls.Control.Background%2A>プロパティ。 `OnBackColorChange`既定のプロパティ マッピングが適用された後、メソッドが呼び出されます。

## <a name="initialize-your-property-mappings"></a>プロパティ マッピングを初期化します。

1. 定義に次のコードをコピー、`Form1`クラス。

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     `Form1_Load`メソッド ハンドル、<xref:System.Windows.Forms.Form.Load>イベントと、次の初期化を実行します。

    - 作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>要素。

    - プロパティ マッピングを設定するチュートリアルの前半で定義されているメソッドを呼び出します。

    - マップされたプロパティに初期値を割り当てます。

2. F5 キーを押してアプリケーションをビルドし、実行します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: Windows フォームでの WPF 複合コントロールをホストしています。](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
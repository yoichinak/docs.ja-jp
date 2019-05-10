---
title: 'チュートリアル: ハイブリッド アプリケーションのローカライズ'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 86779197004f2a8e84d44aaeff2df2dacb05fb01
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621209"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>チュートリアル: ハイブリッド アプリケーションのローカライズ

このチュートリアルは、ローカライズする方法を示します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内の要素を[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-ベースのハイブリッド アプリケーション。

このチュートリアルでは、以下のタスクを行います。

- 作成、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ホスト プロジェクト。

- ローカライズ可能なコンテンツを追加します。

- ローカライズを有効にします。

- リソース識別子を割り当てます。

- LocBaml ツールを使用して、サテライト アセンブリを生成します。

このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。[ハイブリッド アプリケーションのサンプルのローカライズ](https://go.microsoft.com/fwlink/?LinkID=160015)します。

完了したら、ローカライズされたハイブリッド アプリケーションを必要があります。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Windows フォームのホスト プロジェクトの作成

作成するには、まず、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション プロジェクトを追加、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカライズがコンテンツを持つ要素。

### <a name="to-create-the-host-project"></a>ホスト プロジェクトを作成するには

1. 作成、 **WPF アプリ**という名前のプロジェクト`LocalizingWpfInWf`します。  (**ファイル** > **新しい** > **プロジェクト** > **Visual c#** または**Visual Basic**  > **クラシック デスクトップ** > **WPF アプリケーション**)。

2. 追加、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>と呼ばれる要素`SimpleControl`をプロジェクトにします。

3. 使用して、<xref:System.Windows.Forms.Integration.ElementHost>コントロールを配置する、`SimpleControl`フォームの要素。 詳細については、「[チュートリアル:Windows フォームでの 3d WPF 複合コントロールをホストしている](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)します。

## <a name="adding-localizable-content"></a>ローカライズ可能なコンテンツを追加します。

次に、追加、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのラベルし、設定、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素のコンテンツをローカライズ可能な文字列。

### <a name="to-add-localizable-content"></a>ローカライズ可能なコンテンツを追加するには

1. **ソリューション エクスプ ローラー**、ダブルクリックして**SimpleControl.xaml**で開く、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]します。

2. コンテンツを設定、<xref:System.Windows.Controls.Button>次のコードを使用して制御します。

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. **ソリューション エクスプ ローラー**、ダブルクリックして**Form1** Windows フォーム デザイナーで開きます。

4. 開く、**ツールボックス** をダブルクリックします**ラベル**ラベル コントロールをフォームに追加します。 
  <xref:System.Windows.Forms.Control.Text%2A> プロパティの値を `"Hello"` に設定します。

5. **F5** キーを押してアプリケーションをビルドし、実行します。

     両方の`SimpleControl`要素と、ラベル コントロールの表示テキスト **「こんにちは」** します。

## <a name="enabling-localization"></a>ローカライズを有効にします。

Windows フォーム デザイナーでは、サテライト アセンブリでのローカライズを有効にするための設定を提供します。

### <a name="to-enable-localization"></a>ローカライズを有効にするには

1. **ソリューション エクスプ ローラー**、ダブルクリックして**Form1.cs** Windows フォーム デザイナーで開きます。

2. **プロパティ**ウィンドウで、フォームの値を設定する**Localizable**プロパティを`true`します。

3. **プロパティ**ウィンドウで、設定の値、**言語**プロパティを**スペイン語 (スペイン)** します。

4. Windows フォーム デザイナーでは、ラベル コントロールを選択します。

5. **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`"Hola"`します。

     Form1.es ES.resx をという名前の新しいリソース ファイルは、プロジェクトに追加されます。

6. **ソリューション エクスプ ローラー**を右クリックして**Form1.cs**クリック**コードの表示**コード エディターで開きます。

7. 次のコードをコピー、`Form1`への呼び出しの前のコンス トラクター`InitializeComponent`します。

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. **ソリューション エクスプ ローラー**を右クリックして**LocalizingWpfInWf**クリック**プロジェクトのアンロード**します。

     プロジェクト名のラベルは **(利用不可)** します。

9. 右クリックして**LocalizingWpfInWf**、 をクリック**編集 LocalizingWpfInWf.csproj**します。

     プロジェクト ファイルがコード エディターで開きます。

10. 最初に、次の行をコピー`PropertyGroup`プロジェクト ファイル。

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. プロジェクト ファイルを保存して閉じます。

12. **ソリューション エクスプ ローラー**を右クリックして**LocalizingWpfInWf**クリック**プロジェクトの再読み込み**します。

## <a name="assigning-resource-identifiers"></a>リソース識別子を割り当てる

リソース識別子を使用して、リソース アセンブリに、ローカライズ可能なコンテンツをマップできます。 指定するときに MsBuild.exe アプリケーションがリソース識別子に自動的に割り当てられます、`updateuid`オプション。

### <a name="to-assign-resource-identifiers"></a>リソースの識別子を割り当てます

1. [スタート] メニューから Visual Studio 用開発者コマンド プロンプトを開きます。

2. 次のコマンドを使用して、ローカライズ可能なコンテンツへのリソースの識別子を割り当てます。

    ```
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. **ソリューション エクスプ ローラー**、ダブルクリックして**SimpleControl.xaml**コード エディターで開きます。 わかりますが、`msbuild`コマンドが追加、`Uid`属性をすべての要素。 これには、リソース識別子の割り当てを通じてローカライズが容易になります。

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. キーを押して**F6**ソリューションをビルドします。

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>LocBaml を使用してサテライト アセンブリを生成するには

リソース専用で、ローカライズされたコンテンツが格納されている*サテライト アセンブリ*します。 ローカライズされたアセンブリを生成するために、コマンド ライン ツール LocBaml.exe を使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。

### <a name="to-produce-a-satellite-assembly"></a>サテライト アセンブリを生成するには

1. LocBaml.exe をプロジェクトの \debug フォルダーにコピーします。 詳細については、次を参照してください。[アプリケーションをローカライズする](how-to-localize-an-application.md)します。

2. コマンド プロンプト ウィンドウで、次のコマンドを使用して、一時ファイルにリソース文字列を抽出します。

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Visual Studio または他のテキスト エディターで temp.csv ファイルを開きます。 文字列に置き換えます`"Hello"`スペイン語に翻訳を`"Hola"`します。

4. Temp.csv ファイルを保存します。

5. ローカライズされたリソース ファイルを生成するのにには、次のコマンドを使用します。

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     LocalizingWpfInWf.g.es ES.resources ファイルは \debug フォルダーに作成されます。

6. ローカライズされたサテライト アセンブリをビルドするのにには、次のコマンドを使用します。

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     LocalizingWpfInWf.resources.dll ファイルは \debug フォルダーに作成されます。

7. LocalizingWpfInWf.resources.dll ファイルをプロジェクトの bin\Debug\es ES フォルダーにコピーします。 既存のファイルを置き換えます。

8. プロジェクトの bin \debug フォルダーにある LocalizingWpfInWf.exe を実行します。 アプリケーションを再構築しないまたはサテライト アセンブリは上書きされます。

     アプリケーションは、英語の文字列ではなく、ローカライズされた文字列を示しています。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [アプリケーションをローカライズする](how-to-localize-an-application.md)
- [チュートリアル: Windows フォームのローカリゼーション](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)

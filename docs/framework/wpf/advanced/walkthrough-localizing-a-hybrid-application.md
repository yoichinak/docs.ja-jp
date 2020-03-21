---
title: 'チュートリアル : ハイブリッド アプリケーションのローカライズ'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111115"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>チュートリアル : ハイブリッド アプリケーションのローカライズ

このチュートリアルでは、Windows フォーム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ベースのハイブリッド アプリケーションで要素をローカライズする方法を示します。

このチュートリアルでは、以下のタスクを行います。

- Windows フォーム ホスト プロジェクトを作成します。

- ローカライズ可能なコンテンツを追加しています。

- ローカライズを有効にします。

- リソース識別子の割り当て。

- LocBaml ツールを使用して、サテライト アセンブリを生成します。

このチュートリアルで説明するタスクの完全なコードリストについては、「ハイブリッド[アプリケーションのサンプルのローカライズ](https://go.microsoft.com/fwlink/?LinkID=160015)」を参照してください。

完了すると、ローカライズされたハイブリッド アプリケーションが作成されます。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Windows フォーム ホスト プロジェクトの作成

最初の手順では、Windows フォーム アプリケーション プロジェクトを作成[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]し、ローカライズするコンテンツを含む要素を追加します。

### <a name="to-create-the-host-project"></a>ホスト プロジェクトを作成するには

1. という名前の**WPF** `LocalizingWpfInWf`アプリケーション プロジェクトを作成します。  (**ファイル** > **新しい** > **プロジェクト** > **Visual C#** または Visual **Basic** > クラシック**デスクトップ** > WPF**アプリケーション**)

2. プロジェクトに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>呼び`SimpleControl`出される要素を追加します。

3. コントロールを<xref:System.Windows.Forms.Integration.ElementHost>使用して、フォーム`SimpleControl`上に要素を配置します。 詳細については、「[チュートリアル : Windows フォームでの 3D WPF 複合コントロールのホスト](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)」を参照してください。

## <a name="adding-localizable-content"></a>ローカライズ可能なコンテンツの追加

次に、Windows フォーム のラベル コントロールを追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]し、要素の内容をローカライズ可能な文字列に設定します。

### <a name="to-add-localizable-content"></a>ローカライズ可能なコンテンツを追加するには

1. **ソリューション エクスプローラー**で、 **SimpleControl.xaml**をダブルクリックして、WPF デザイナーで開きます。

2. 次のコードを使用<xref:System.Windows.Controls.Button>して、コントロールの内容を設定します。

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. **ソリューション エクスプローラー**で **、[Form1]** をダブルクリックして Windows フォーム デザイナーで開きます。

4. **ツールボックス**を開き、[**ラベル**] をダブルクリックして、フォームにラベル コントロールを追加します。 <xref:System.Windows.Forms.Control.Text%2A> プロパティの値を `"Hello"` に設定します。

5. **F5 キー**を押してアプリケーションをビルドし、実行します。

     `SimpleControl`要素とラベル コントロールの両方に **"Hello"** というテキストが表示されます。

## <a name="enabling-localization"></a>ローカリゼーションの有効化

Windows フォーム デザイナーには、サテライト アセンブリのローカライズを有効にするための設定が用意されています。

### <a name="to-enable-localization"></a>ローカリゼーションを有効にするには

1. **ソリューション エクスプローラー**で **、Form1.cs**をダブルクリックして、Windows フォーム デザイナーで開きます。

2. [**プロパティ]** ウィンドウで、フォームの **"ローカライズ可能**" プロパティの値を`true`に設定します。

3. [**プロパティ**] ウィンドウで **、Language**プロパティの値を**スペイン語 (スペイン)** に設定します。

4. Windows フォーム デザイナーで、ラベル コントロールを選択します。

5. [**プロパティ]** ウィンドウで、プロパティの値<xref:System.Windows.Forms.Control.Text%2A>を`"Hola"`に設定します。

     Form1.es-ES.resx という名前の新しいリソース ファイルがプロジェクトに追加されます。

6. **ソリューション エクスプローラー**で **、Form1.cs**を右クリックし、[**コードの表示**] をクリックしてコード エディターで開きます。

7. コンストラクターに次のコードを`Form1`コピーします`InitializeComponent`。

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. **ソリューション エクスプローラー**で **、[LocalizingWpfInWf]** を右クリックし、[**プロジェクトのアンロード**] をクリックします。

     プロジェクト名には、(**利用不可)** というラベルが付いています。

9. を右クリックし、[**ローカライズするWpfInWf.csproj**の編集] をクリックします。 **LocalizingWpfInWf**

     プロジェクト ファイルがコード エディターで開きます。

10. 次の行をプロジェクト ファイル`PropertyGroup`の最初の行にコピーします。

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. プロジェクト ファイルを保存して閉じます。

12. **ソリューション エクスプローラー**で **、[LocalizingWpfInWf]** を右クリックし、[**プロジェクトの再読み込み**] をクリックします。

## <a name="assigning-resource-identifiers"></a>リソース識別子の割り当て

リソース識別子を使用して、ローカライズ可能なコンテンツをリソース アセンブリにマップできます。 MsBuild.exe アプリケーションは、オプションを指定すると、リソース識別子を`updateuid`自動的に割り当てます。

### <a name="to-assign-resource-identifiers"></a>リソース識別子を割り当てるには

1. [スタート] メニューから、Visual Studio の開発者コマンド プロンプトを開きます。

2. 次のコマンドを使用して、ローカライズ可能なコンテンツにリソース識別子を割り当てます。

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. **ソリューション エクスプローラー**で **、SimpleControl.xaml**をダブルクリックしてコード エディターで開きます。 コマンドがすべての要素に`msbuild`属性を`Uid`追加したことがわかります。 これにより、リソース識別子の割り当てによってローカリゼーションが容易になります。

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. **F6** キーを押して、ソリューションをビルドします。

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>LocBaml を使用したサテライト アセンブリの生成

ローカライズされたコンテンツは、 リソース専用サ*テライト アセンブリ*に格納されます。 コンテンツ用のローカライズされたアセンブリを生成するには、コマンド ライン ツール LocBaml.exe を使用します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。

### <a name="to-produce-a-satellite-assembly"></a>サテライト アセンブリを作成するには

1. LocBaml.exe をプロジェクトの obj\Debug フォルダーにコピーします。 詳細については、「[アプリケーションのローカライズ](how-to-localize-an-application.md)」を参照してください。

2. コマンド プロンプト ウィンドウで、次のコマンドを使用して、リソース文字列を一時ファイルに抽出します。

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Visual Studio または別のテキスト エディターで temp.csv ファイルを開きます。 文字列`"Hello"`をスペイン語の翻訳に置`"Hola"`き換えます。

4. temp.csv ファイルを保存します。

5. ローカライズされたリソース ファイルを生成するには、次のコマンドを使用します。

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     LocalizingWpfInWf.g.es-ES.resources ファイルは obj\Debug フォルダーに作成されます。

6. ローカライズされたサテライト アセンブリをビルドするには、次のコマンドを使用します。

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     ファイルは obj\デバッグ フォルダーに作成されます。

7. プロジェクトの bin\Debug\es-ES フォルダーにローカライズWpfInWf.resources.dll ファイルをコピーします。 既存のファイルを置き換えます。

8. プロジェクトの bin\Debug フォルダーにあるローカライズWpfInWf.exe を実行します。 アプリケーションを再構築しないか、サテライト アセンブリが上書きされます。

     アプリケーションは、英語の文字列の代わりにローカライズされた文字列を表示します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [アプリケーションのローカライズ](how-to-localize-an-application.md)
- [チュートリアル : Windows フォームのローカリゼーション](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Visual Studio で XAML をデザインする](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)

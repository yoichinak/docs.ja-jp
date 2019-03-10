---
title: '方法: Windows フォームに ActiveX コントロールを追加します。'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 68e25cb2cd7e1f1c63954b20d24f028a49431553
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707990"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>方法: Windows フォームに ActiveX コントロールを追加します。
Windows フォーム コントロールをホストするには、Windows フォーム デザイナーが最適化され、中には、Windows フォームで ActiveX コントロールも記述できます。  
  
> [!CAUTION]
>  ActiveX コントロールを追加することがある場合に、Windows フォームのパフォーマンスの制限があります。  
  
 ActiveX コントロールをフォームに追加する前に、ツールボックスに追加する必要があります。 詳細については、次を参照してください。 [COM コンポーネント、ツールボックスのカスタマイズ ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100))します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Windows フォームに ActiveX コントロールを追加するには  
  
-   ツールボックスにコントロールをダブルクリックします。  
  
     Visual Studio では、プロジェクトのコントロールにすべての参照を追加します。 Windows フォームで ActiveX コントロールを使用する場合に留意すべき点の詳細については、次を参照してください。 [Windows フォームで ActiveX コントロールをホストしている場合の考慮事項](considerations-when-hosting-an-activex-control-on-a-windows-form.md)します。  
  
    > [!NOTE]
    >  Windows フォーム ActiveX コントロール インポーター (AxImp.exe) は、ActiveX のダイナミック リンク ライブラリのインポート時に予想よりも、別の種類のイベント引数を作成します。 AxImp.exe によって作成された引数は、次のような: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`、`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`が必要です。 この不規則性から正常に機能して、コードが回避しないことに注意します。 詳細については、次を参照してください。 [Windows フォーム ActiveX コントロール インポーター (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)します。  
  
## <a name="see-also"></a>関連項目
- [Windows フォーム コントロール](index.md)
- [各言語およびライブラリにおける、コントロールとプログラミング可能オブジェクトの比較](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [方法: Windows フォームにコントロールを追加します。](how-to-add-controls-to-windows-forms.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)

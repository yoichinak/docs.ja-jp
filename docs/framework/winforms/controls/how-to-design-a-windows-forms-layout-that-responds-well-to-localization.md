---
title: '方法: ローカリゼーションに対応した Windows フォーム レイアウトをデザインする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 095427ce633ee6db5a448c8f3f69304ed25ab82a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142598"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>方法: ローカリゼーションに対応した Windows フォーム レイアウトをデザインする
ローカライズが可能なフォームを作成すると、各国市場向けの開発期間が大幅に短縮されます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、<xref:System.Windows.Forms.Control.Text%2A> プロパティ値の変更によってコントロールのサイズが変更された際に、これに適切に応答するレイアウトを実装できます  
  
## <a name="example"></a>例  
 このフォームでは、表示される文字列値を他の言語に翻訳するときに、均等に調整されるレイアウトを作成する方法を示します。 この翻訳プロセスのことを "*ローカリゼーション*" といいます。 詳細については、「[ローカリゼーション](../../../standard/globalization-localization/localization.md)」を参照してください。  
  
 Visual Studio では、このタスクに対する広範なサポートが用意されています。  参照してください[チュートリアル。ローカライズの縦横比が調整されるレイアウトの作成](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))です。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>その他の技術情報
1.  [方法: TableLayoutPanel コントロール内でコントロールを配置して伸縮する](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3.  [方法: TableLayoutPanel コントロールの行と列を拡大する](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [方法: TableLayoutPanel コントロールの列と行を編集する](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  [チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6.  [チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7.  [チュートリアル: Padding、Margin、AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](windows-forms-controls-padding-autosize.md)  
  
8.  [方法: AutoSize と TableLayoutPanel コントロールを使用して Windows フォームのローカリゼーションをサポートします。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [チュートリアル: データ エントリのサイズ変更可能な Windows フォームを作成します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [ローカリゼーション](../../../standard/globalization-localization/localization.md)

---
title: '方法: TableLayoutPanel コントロールの列と行を編集します。'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 40129deed1f43480b7bde59ef8a67f4561af5d38
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724688"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>方法: TableLayoutPanel コントロールの列と行を編集します。
コレクション エディターを使用することができます、<xref:System.Windows.Forms.TableLayoutPanel>というコントロール、**列と行のスタイル**行と、コントロールの列を編集するためのダイアログ ボックス。  
  
> [!NOTE]
>  コントロールに複数の行または列にまたがる場合は、設定、`RowSpan`と`ColumnSpan`コントロールのプロパティ。 詳細については、「[チュートリアル:TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)します。  
>   
>  セル内のコントロールを配置する場合、またはコントロールのセル内をしたい場合を使用して、コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ。 詳細については、「[チュートリアル:TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)します。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-edit-rows-and-columns"></a>行と列を編集するには  
  
1.  <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2.  をクリックして、<xref:System.Windows.Forms.TableLayoutPanel>コントロールのスマート タグ グリフ (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) を選択して**編集行と列**を開く、 **列と行のスタイル** ダイアログ ボックス。 クリックすることも右に、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、選択**編集行と列**ショートカット メニューから。  
  
3.  列を追加または削除、選択**列**から、**メンバーの種類**ドロップダウン リスト ボックス。  
  
4.  を追加または削除行に次のように選択します。**行**から、**メンバーの種類**ドロップダウン リスト ボックス。  
  
5.  をクリックして、**追加**の末尾に行または列を追加するボタン、**メンバー**一覧。  
  
6.  をクリックして、**挿入**の一覧で行または現在選択されている項目の前に列を追加するボタンをクリックします。  
  
7.  行または列を追加する場合は、選択、**サイズ型**新しい行または列。 詳細については、「 <xref:System.Windows.Forms.SizeType> 」を参照してください。  
  
8.  行または列を削除する をクリックして、**削除**で現在選択されている項目を削除するボタン、**メンバー**一覧。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel コントロール](tablelayoutpanel-control-windows-forms.md)

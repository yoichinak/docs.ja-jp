---
title: '方法: デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: e87017f3698bc88a123d8a0ba0df5dbe2b7bbfd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314868"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する
Windows フォームに既に追加されている列の型を変更することがありますする<xref:System.Windows.Forms.DataGridView>コントロール。 たとえば、一部のコントロールをデータ ソースにバインドすると、自動的に生成される列の型を変更したい場合があります。 これは、関連テーブル内の行を外部キーを含む列を表示するテーブルがある場合に便利です。 この場合、関連テーブルから意味のある値を表示するコンボ ボックスの列と、これらの外部キーを表示するテキスト ボックスの列を置換することがあります。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>デザイナーを使用して、列の種類を変更するには  
  
1. スマート タグ グリフをクリックします (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、 <xref:System.Windows.Forms.DataGridView> 、制御し、**列の編集**します。  
  
2. 列を選択、**選択した列**一覧。  
  
3. **列プロパティ**グリッドで、設定、`ColumnType`プロパティを新しい列の型。  
  
    > [!NOTE]
    >  `ColumnType`プロパティは、設計時専用のプロパティで、列の型を表すクラスを示します。 列のクラスで定義されている実際のプロパティではありません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: Windows フォームにコントロールを追加します。](how-to-add-controls-to-windows-forms.md)

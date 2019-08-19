---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: d38c8d73bc70e7e521b476ca78c8f102d003c538
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040335"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する
ユーザーが Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールに表示されるデータを確認するときに、1 つの列または列のセットを頻繁に参照しなければならないことがあります。 たとえば、多数の列が含まれている顧客情報のテーブルを表示する場合、他の列を表示可能な領域の外側にスクロールできるようにしながら、常に顧客名を表示すると便利です。

 この動作を実現するために、コントロールの列を固定することができます。 列を固定すると、左側 (右から左へ記述する言語のスクリプトでは右側) のすべての列も同様に固定されます。 固定された列は表示されたままになり、その他のすべての列はスクロールできます。 列の並べ替えが有効な場合、固定された列は、固定されていない列とは異なるグループとして扱われます。 ユーザーは、どちらかのグループに列を再配置できますが、1 つのグループから別のグループに列を移動することはできません。

 次の手順では、 <xref:System.Windows.Forms.DataGridView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

## <a name="to-freeze-a-column-using-the-designer"></a>デザイナーを使用して列を固定するには

1. <xref:System.Windows.Forms.DataGridView>コントロールの右上隅にあるスマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) をクリックし、 **[列の編集]** を選択します。

2. **[選択された列]** ボックスの一覧から列を選択します。

3. 列の**プロパティ**グリッドで、 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A>プロパティをに`true`設定します。

    > [!NOTE]
    >  **[列の追加]** ダイアログボックスで**固定**されたボックスを選択して、列を追加するときに固定することもできます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [方法: デザイナーを使用した Windows フォーム DataGridView コントロールでの列の追加と削除](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールで列の並べ替えを有効にする](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [方法: グローバリゼーション用に Windows フォームに右から左に記述するテキストを表示する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: コントロールを Windows フォームに追加する](how-to-add-controls-to-windows-forms.md)

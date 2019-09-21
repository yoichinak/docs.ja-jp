---
title: '方法: デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 82be9d31ff6bb3f2f5dd8a55b4426103d466bdd6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952092"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする
既定では、ユーザーは Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールに表示されるテキストおよび数値データを変更できます。 変更を意図していないデータを表示する場合は、データを含む列を読み取り専用にする必要があります。 コントロールを完全に読み取り専用にする方法については、 [「方法:デザイナー](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)を使用して Windows フォーム DataGridView コントロールで行の追加と削除を防止します。

 次の手順では、 <xref:System.Windows.Forms.DataGridView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>デザイナーを使用して列を読み取り専用にするには

1. <xref:System.Windows.Forms.DataGridView>コントロールの右上隅にあるスマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) をクリックし、 **[列の編集]** を選択します。

2. **[選択された列]** ボックスの一覧から列を選択します。

3. 列の**プロパティ**グリッドで、 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>プロパティをに`true`設定します。

    > [!NOTE]
    > また、 **[列の追加]** ダイアログボックスの **[読み取り専用]** チェックボックスをオンにすると、列を追加するときに読み取り専用にすることもできます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [方法: デザイナーを使用した Windows フォーム DataGridView コントロールでの列の追加と削除](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールで行の追加と削除を防止する](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: コントロールを Windows フォームに追加する](how-to-add-controls-to-windows-forms.md)

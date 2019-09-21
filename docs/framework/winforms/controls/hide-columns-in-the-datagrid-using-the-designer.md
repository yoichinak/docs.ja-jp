---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を非表示にする'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 35aa1cdeef919d4267cb27da79f183c4c52aefa2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916387"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を非表示にする
Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールで使用できる列の一部のみを表示したいときがあります。 たとえば、管理資格情報を持つユーザーに employee salary 列を表示し、他のユーザーには表示しないようにすることができます。 または、いくつかの列を含むデータソースにコントロールをバインドし、その一部のみを表示することもできます。 この場合、通常は、表示されていない列を非表示にするのではなく、削除します。 詳細については、「[方法 :デザイナー](add-and-remove-columns-in-the-datagrid-using-the-designer.md)を使用して Windows フォーム DataGridView コントロールの列を追加および削除します。

 次の手順では、 <xref:System.Windows.Forms.DataGridView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

## <a name="to-hide-a-column-using-the-designer"></a>デザイナーを使用して列を非表示にするには

1. <xref:System.Windows.Forms.DataGridView>コントロールの右上隅にあるスマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) をクリックし、 **[列の編集]** を選択します。

2. **[選択された列]** ボックスの一覧から列を選択します。

3. 列の**プロパティ**グリッドで、 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>プロパティをに`false`設定します。

    > [!NOTE]
    > **[列の追加]** ダイアログボックスの **[表示]** チェックボックスをオフにすることで、列を追加するときに非表示にすることもできます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [方法: デザイナーを使用した Windows フォーム DataGridView コントロールでの列の追加と削除](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: コントロールを Windows フォームに追加する](how-to-add-controls-to-windows-forms.md)

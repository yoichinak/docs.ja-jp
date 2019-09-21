---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039633"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する

Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールをデータソースにバインドすると、自動的に生成された列の表示順序はデータソースによって決まります。 この順序が希望どおりでない場合は、デザイナーを使用して列の順序を変更できます。 コントロールに非バインド列を追加して、表示順序を変更することもできます。 プログラムによって列の順序を変更する方法の[詳細については、「方法:Windows フォーム DataGridView コントロール](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)の列の順序を変更します。

次の手順では、 <xref:System.Windows.Forms.DataGridView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

## <a name="to-change-the-column-order-using-the-designer"></a>デザイナーを使用して列の順序を変更するには

1. <xref:System.Windows.Forms.DataGridView>コントロールの右上隅にあるスマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) をクリックし、 **[列の編集]** を選択します。

2. **[選択された列]** ボックスの一覧から列を選択します。

3. [**選択さ**れた列] の一覧の右側にある上矢印または下矢印をクリックすると、選択した列が目的の位置に表示されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [方法: デザイナーを使用した Windows フォーム DataGridView コントロールでの列の追加と削除](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: コントロールを Windows フォームに追加する](how-to-add-controls-to-windows-forms.md)

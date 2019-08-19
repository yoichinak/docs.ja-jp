---
title: '方法: デザイナーを使って Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040363"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>方法: デザイナーを使って Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする
<xref:System.Windows.Forms.ListView>コントロールのタイルビュー機能を使用すると、グラフィカルな情報とテキスト情報の間に視覚的なバランスを取ることができます。 並べて表示ビューの項目で表示されるテキスト情報は、詳細ビュー用に定義されている列情報と同じ情報です。 並べて表示ビューは、 <xref:System.Windows.Forms.ListView>コントロールのグループ化機能または挿入マーク機能と組み合わせて使用します。

 タイルビューでは、次の図に示すように、32 x 32 アイコンと数行のテキストが使用されます。

 ![ListView コントロールのタイルビュー](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "タイルビューのアイコンとテキスト")

 タイルビューのプロパティとメソッドを使用すると、各項目に対して表示する列フィールドを指定したり、タイルビューウィンドウ内のすべての項目のサイズと外観をまとめて制御したりすることができます。 わかりやすくするために、タイルのテキストの最初の行は常に項目の名前です。変更することはできません。

 次の手順では、 <xref:System.Windows.Forms.ListView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

> [!NOTE]
> 並べて表示ビューを [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] で使用できるのは、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> メソッドを呼び出した場合だけです。 旧バージョンのオペレーティング システムでは、並べて表示ビューに関するコードがすべて無効になり、<xref:System.Windows.Forms.ListView> コントロールは大きなアイコンのビューで表示されます。 詳細については、「 <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType> 」を参照してください。

## <a name="to-set-tile-view-in-the-designer"></a>デザイナーでタイルビューを設定するには

1. Visual Studio で、フォーム上<xref:System.Windows.Forms.ListView>のコントロールを選択します。

2. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.ListView.View%2A>プロパティを選択し、 **[タイル]** を選択します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView コントロールの概要](listview-control-overview-windows-forms.md)

---
title: '方法: デザイナーを使用して Windows フォーム ListView コントロールの項目をグループ化'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 4c3e20ad7a09cc21e6c1d2a6d8fbbc47d11c903d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703557"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム ListView コントロールの項目をグループ化
グループ化機能、<xref:System.Windows.Forms.ListView>コントロールでは、グループ内のアイテムの関連する設定を表示することができます。 これらのグループは、画面に含まれるグループのタイトルは水平方向のグループ ヘッダーで区切られます。 使用することができます<xref:System.Windows.Forms.ListView>グループ日付、または他の論理グループで、アルファベット順に項目をグループ化して簡単に大きい一覧を移動します。 次の図には、いくつかのグループ化された項目が表示されます。  
  
 ![ListView グループ](./media/listviewgroups.gif "ListViewGroups")  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.ListView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
 グループ化を有効にする必要があります最初に作成する 1 つまたは複数<xref:System.Windows.Forms.ListViewGroup>オブジェクトがデザイナーで、またはプログラムを使用します。 グループを定義した後に項目を割り当てることができます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> のみ使用可能なグループ[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]、アプリケーションを呼び出すと、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>メソッド。 以前のオペレーティング システムでは、グループに関するすべてのコードが影響を与えません、グループは表示されません。 詳細については、「 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType> 」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>追加またはデザイナーでグループを削除するには  
  
1.  **プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.ListView.Groups%2A>プロパティ。  
  
     **ListViewGroup コレクション エディター**が表示されます。  
  
2.  グループを追加する をクリックして、**追加**ボタンをクリックします。 など、新しいグループのプロパティを設定することができますし、<xref:System.Windows.Forms.ListViewGroup.Header%2A>と<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>プロパティ。 グループを削除するを選択し、クリックして、**削除**ボタンをクリックします。  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>デザイナーでのグループに項目を割り当てる  
  
1.  **プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.ListView.Items%2A>プロパティ。  
  
     **ListViewItem コレクション エディター**が表示されます。  
  
2.  新しいアイテムを追加する をクリックして、**追加**ボタンをクリックします。 など、新しい項目のプロパティを設定することができますし、<xref:System.Windows.Forms.ListViewItem.Text%2A>と<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>プロパティ。  
  
3.  選択、<xref:System.Windows.Forms.ListViewItem.Group%2A>プロパティ ドロップダウン リストからグループを選択します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView コントロール](listview-control-windows-forms.md)
- [ListView コントロールの概要](listview-control-overview-windows-forms.md)
- [方法: Windows フォーム ListView コントロールで項目追加および削除](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)

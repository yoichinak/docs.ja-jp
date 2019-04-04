---
title: '方法: デザイナーを使用して、BindingSource コンポーネントを使用した Windows フォーム コントロールをバインドします。'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: e12498bc71957d49893e49e54095b6bb184ac2c3
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441919"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>方法: デザイナーを使用して、BindingSource コンポーネントを使用した Windows フォーム コントロールをバインドします。
コントロールがフォームに追加し、アプリケーションのユーザー インターフェイスを決定したら後、は、実行時に、ユーザーは変更して、アプリケーションに関連するデータを保存できるように、データ ソースにコントロールをバインドできます。  
  
 使用して最も簡単に実現は、Windows フォーム コントロールまたは一連のコントロールをバインドする、<xref:System.Windows.Forms.BindingSource>コントロールをフォーム上のコントロールとデータ ソース間のブリッジとして。  
  
 フォーム上の 1 つまたは複数のコントロールをデータにバインドできます。次の手順で、<xref:System.Windows.Forms.TextBox>コントロールがデータ ソースにバインドします。  
  
 データベースから取得したデータ ソースにバインドすることは、手順を完了するには、と見なされます。 その他のデータ ストアからデータ ソースを作成する方法の詳細については、[新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-bind-a-control-at-design-time"></a>デザイン時にコントロールをバインドするには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TextBox>コントロールをフォームにログオンします。  
  
2.  **プロパティ**ウィンドウ。  
  
    1.  展開、 **(DataBindings)** ノード。  
  
    2.  矢印をクリックして、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティ。  
  
         **DataSource** UI 型エディターを開きます。  
  
         プロジェクトまたはフォームのデータ ソースが構成されていた場合は、表示されます。  
  
3.  **[プロジェクト データ ソースの追加]** をクリックしてデータに接続し、データ ソースを作成します。  
  
4.  **データ ソース構成ウィザード**の開始ページで **[次へ]** をクリックします。  
  
5.  **データ ソースの種類を選択**] ページで、[**データベース**します。  
  
6.  **データ接続の選択** ページで、利用可能な接続の一覧からデータ接続を選択します。 目的のデータ接続が使用可能な選択ではない場合**新しい接続**新しいデータ接続を作成します。  
  
7.  選択**接続を [はい] に、保存**をアプリケーション構成ファイルで接続文字列を保存します。  
  
8.  アプリケーションで使用するデータベース オブジェクトを選択します。 この場合、希望するテーブルでフィールドを選び、<xref:System.Windows.Forms.TextBox>を表示します。  
  
9. 必要な場合は、既定のデータセット名を変更します。  
  
10. **[完了]** をクリックします。  
  
11. **プロパティ**ウィンドウで、矢印をクリックして、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティを再度します。 **DataSource** UI 型エディターでは、バインドするフィールドの名前を選択する、<xref:System.Windows.Forms.TextBox>にします。  
  
     **DataSource** UI 型エディターが終了し、データ セット<xref:System.Windows.Forms.BindingSource>およびテーブル アダプターをフォームにデータ接続が追加されたことを特定します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)
- [データ ソース ウィンドウ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
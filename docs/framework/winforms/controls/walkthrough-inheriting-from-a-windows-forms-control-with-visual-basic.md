---
title: 'チュートリアル: Visual Basic による Windows フォーム コントロールからの継承'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: c7e4f49fa5bd4de1e15e8f3cf39b95779c33ef94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087067"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>チュートリアル: Visual Basic による Windows フォーム コントロールからの継承
Visual basic の場合は、使用して強力なカスタム コントロールを作成できます*継承*します。 継承を使用すると、標準の Windows フォーム コントロールの固有の機能をすべて保持しながら、カスタム機能も組み込んだコントロールを作成できます。 このチュートリアルでは、`ValueButton` という単純な継承されたコントロールを作成します。 このボタンは、標準の Windows フォームから機能を継承<xref:System.Windows.Forms.Button>、制御し、という名前のカスタム プロパティを公開`ButtonValue`します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 新しいプロジェクトを作成するときは、ルート名前空間、アセンブリ名、プロジェクト名を設定し、既定のコンポーネントが適切な名前空間に含まれるようにするために、プロジェクトの名前を指定します。  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>ValueButtonLib コントロール ライブラリと ValueButton コントロールを作成するには  
  
1.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログ ボックスを開きます。  
  
2.  選択、 **Windows フォーム コントロール ライブラリ**Visual Basic プロジェクト、および種類の一覧からプロジェクト テンプレート`ValueButtonLib`で、**名前**ボックス。  
  
     プロジェクト名 `ValueButtonLib` は、既定でルート名前空間にも割り当てられます。 ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。 たとえば、`ValueButton` という名前のコンポーネントが 2 つのアセンブリに含まれている場合、`ValueButtonLib.ValueButton` を使用して目的の `ValueButton` コンポーネントを指定できます。 詳細については、「[Visual Basic における名前空間](~/docs/visual-basic/programming-guide/program-structure/namespaces.md)」を参照してください。  
  
3.  **ソリューション エクスプローラー**で、**[UserControl1.vb]** を右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。 ファイル名を `ValueButton.vb` に変更します。 コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。  
  
4.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。  
  
5.  **[ValueButton.vb]** ノードを開いて、デザイナーによって生成されたコード ファイル (**ValueButton.Designer.vb**) を表示します。 このファイルを**コード エディター**で開きます。  
  
6.  検索、`Class`ステートメントでは、 `Partial Public Class ValueButton`、このコントロールから継承する型を変更および<xref:System.Windows.Forms.UserControl>に<xref:System.Windows.Forms.Button>します。 これにより、継承されたコントロールのすべての機能を継承するように、<xref:System.Windows.Forms.Button>コントロール。  
  
7.  検索、`InitializeComponent`メソッドと remove を割り当てる行、<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>プロパティ。 このプロパティに存在しません、<xref:System.Windows.Forms.Button>コントロール。  
  
8.  **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
     ビジュアル デザイナーは使用できなくなっていることに注意してください。 <xref:System.Windows.Forms.Button>コントロールは独自の描画、デザイナーでは、その外観を変更することがないです。 ビジュアル表現は同じでなければから継承するクラスと (つまり、 <xref:System.Windows.Forms.Button>)、コードで変更しない限り、します。  
  
> [!NOTE]
>  UI 要素のないコンポーネントをデザイン サーフェイスに追加することは可能です。  
  
## <a name="adding-a-property-to-your-inherited-control"></a>継承されたコントロールへのプロパティの追加  
 継承された Windows フォーム コントロールの考えられる用途の 1 つとして、外観と動作 (ルック アンド フィール) は標準の Windows フォーム コントロールと同じでありながら、カスタム プロパティを公開するコントロールの作成があります。 このセクションでは、`ButtonValue` というプロパティをコントロールに追加します。  
  
#### <a name="to-add-the-value-property"></a>Value プロパティを追加するには  
  
1.  **ソリューション エクスプローラー**で、**[ValueButton.vb]** を右クリックし、ショートカット メニューの **[コードの表示]** をクリックします。  
  
2.  `Public Class ValueButton` ステートメントを探します。 このステートメントの直後に、次のコードを追加します。  
  
    ```vb  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     このコードでは、`ButtonValue` プロパティを格納し、取得するメソッドを設定しています。 `Get` ステートメントは、返された値を `varValue` プライベート変数に格納されている値に設定します。`Set` ステートメントは、`Value` キーワードを使用してプライベート変数の値を設定します。  
  
3.  **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
## <a name="testing-your-control"></a>コントロールのテスト  
 コントロールはスタンドアロン プロジェクトではないため、コンテナー内でホストする必要があります。 コントロールをテストするには、コントロールを実行するテスト プロジェクトを指定する必要があります。 また、コントロールをビルド (コンパイル) して、テスト プロジェクトからアクセスできるようにする必要があります。 このセクションでは、コントロールをビルドし、Windows フォームでテストします。  
  
#### <a name="to-build-your-control"></a>コントロールをビルドするには  
  
1.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
     コンパイル エラーも警告も発生せずに、ビルドが正常に完了します。  
  
#### <a name="to-create-a-test-project"></a>テスト プロジェクトを作成するには  
  
1.  **[ファイル]** メニューの **[追加]** をポイントし、**[新しいプロジェクト]** をクリックして **[新しいプロジェクトの追加]** ダイアログ ボックスを開きます。  
  
2.  Visual Basic のプロジェクト ノードを選択し、クリックして**Windows フォーム アプリケーション**します。  
  
3.  **[名前]** ボックスに「 `Test`」と入力します。  
  
4.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。  
  
5.  **ソリューション エクスプローラー**で、テスト プロジェクトの **[参照設定]** ノードを右クリックし、ショートカット メニューの **[参照の追加]** をクリックして **[参照の追加]** ダイアログ ボックスを表示します。  
  
6.  **[プロジェクト]** タブをクリックします。  
  
7.  **[プロジェクト]** というラベルのタブをクリックします。 **[プロジェクト名]** に `ValueButtonLib` プロジェクトが表示されます。 プロジェクトをダブルクリックして、テスト プロジェクトへの参照を追加します。  
  
8.  **ソリューション エクスプローラー**で、**[Test]** を右クリックし、**[ビルド]** をクリックします。  
  
#### <a name="to-add-your-control-to-the-form"></a>コントロールをフォームに追加するには  
  
1.  **ソリューション エクスプローラー**で、**[Form1.vb]** を右クリックし、ショートカット メニューの **[デザイナーの表示]** をクリックします。  
  
2.  **ツールボックス**の **[ValueButtonLib コンポーネント]** をクリックします。 **[ValueButton]** をダブルクリックします。  
  
     **ValueButton** がフォームに表示されます。  
  
3.  **[ValueButton]** を右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。  
  
4.  **[プロパティ]** ウィンドウで、このコントロールのプロパティを調べます。 プロパティは、追加のプロパティである `ButtonValue` がある点を除き、標準ボタンで公開されるプロパティと同じです。  
  
5.  `ButtonValue` プロパティを `5`に設定します。  
  
6.  **すべての Windows フォーム**のタブ、**ツールボックス**、 をダブルクリックします**ラベル**を追加する、<xref:System.Windows.Forms.Label>をフォームにコントロール。  
  
7.  ラベルをフォームの中央に配置し直します。  
  
8.  `ValueButton1` をダブルクリックします。  
  
     **コード エディター**が開き、`ValueButton1_Click` イベントが表示されます。  
  
9. 次のコード行を入力します。  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. **ソリューション エクスプローラー**で、**[Test]** を右クリックし、ショートカット メニューの **[スタートアップ プロジェクトに設定]** をクリックします。  
  
11. **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
     `Form1` 表示されます。  
  
12. [`Valuebutton1`] をクリックします。  
  
     `Label1` に数字の "5" が表示されます。これは、継承されたコントロールの `ButtonValue` プロパティが、`ValueButton1_Click` メソッドによって `Label1` に渡されたことを示しています。 このようにして、`ValueButton` コントロールは標準の Windows フォーム ボタンの機能をすべて継承しながら、追加のカスタム プロパティを公開します。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: Visual Basic による複合コントロールの作成](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
- [継承の基本 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

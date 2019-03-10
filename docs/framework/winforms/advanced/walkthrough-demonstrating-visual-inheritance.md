---
title: 'チュートリアル: ビジュアル継承のデモンストレーション'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: aa4d18c0e3bbc2613502c7232771c57acc7f0dc8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721451"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>チュートリアル: ビジュアル継承のデモンストレーション
ビジュアル継承により、基本フォームのコントロールを表示して、新しいコントロールを追加できます。 このチュートリアルでは、基本フォームを作成してクラス ライブラリにコンパイルします。 このクラス ライブラリを別のプロジェクトにインポートして、基本フォームから継承する新しいフォームを作成します。 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   基本フォームを含むクラス ライブラリ プロジェクトを作成します。  
  
-   基本フォームの派生クラスが変更できるプロパティを持つボタンを追加します。  
  
-   基本フォームの継承元により変更できないボタンを追加します。  
  
-   `BaseForm` から継承したフォームを含むプロジェクトを作成します。  
  
 最終的には、このチュートリアルでは、継承されたフォーム上のプライベート コントロールとプロテクト コントロールの違いを示します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
> [!CAUTION]
>  すべてのコントロールが基本フォームのビジュアル継承をサポートするわけではありません。 次のコントロールでは、このチュートリアルで説明するシナリオはサポートされません。  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  継承されたフォームのこれらのコントロールは、使用する修飾子 (`private`、`protected`、または `public`) に関係なく、常に読み取り専用です。  
  
## <a name="scenario-steps"></a>シナリオの手順  
 最初の手順では、基本フォームを作成します。  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>基本フォームを含むクラス ライブラリ プロジェクトを作成するには  
  
1.  **ファイル** メニューの 選択**新規**、し**プロジェクト**を開く、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  という名前の Windows フォーム アプリケーションを作成する`BaseFormLibrary`します。  
  
3.  標準の Windows フォーム アプリケーションではなくクラス ライブラリを作成する**ソリューション エクスプ ローラー**を右クリックし、 **BaseFormLibrary**プロジェクト ノードを選び**プロパティ**.  
  
4.  プロジェクトのプロパティで、変更、**出力の種類**から**Windows アプリケーション**に**クラス ライブラリ**します。  
  
5.  **ファイル**] メニューの [選択**すべて保存**を既定の場所に、プロジェクトおよびファイルを保存します。  
  
 次の 2 つの手順では、基本フォームにボタンを追加します。 ビジュアル継承を示すには、`Modifiers` プロパティを設定して、ボタンに異なるアクセス レベルを付与します。  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>基本フォームの継承クラスから変更が可能なボタンを追加するには  
  
1.  デザイナーで **Form1** を開きます。  
  
2.  **すべての Windows フォーム**のタブ、**ツールボックス**、ダブルクリック**ボタン**をフォームにボタンを追加します。 マウスを使用し、ボタンを配置してサイズを変更します。  
  
3.  [プロパティ] ウィンドウで、ボタンの次のプロパティを設定します。  
  
    -   設定、**テキスト**プロパティを**Say こんにちは**します。  
  
    -   設定、 **(名)** プロパティを**btnProtected**します。  
  
    -   設定、**修飾子**プロパティを**Protected**します。 継承するフォームが可能になります。 **Form1**のプロパティを変更する**btnProtected**します。  
  
4.  ダブルクリックして、 **Say こんにちは**のイベント ハンドラーを追加するボタン、 **をクリックして**イベント。  
  
5.  イベント ハンドラーに次のコードを追加します。  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>基本フォームの継承元により変更できないボタンを追加するには  
  
1.  クリックしてデザイン ビューに切り替え、 **Form1.vb [デザイン]、Form1.cs [デザイン]、または Form1.jsl の [デザイン]** コード エディターの上または F7 キーを押してタブです。  
  
2.  2 番目のボタンを追加し、そのプロパティを次のように設定します。  
  
    -   設定、**テキスト**プロパティを**Say Goodbye**します。  
  
    -   設定、 **(名)** プロパティを**btnPrivate**します。  
  
    -   設定、**修飾子**プロパティを**プライベート**します。 継承するフォームが不可能になります。 **Form1**のプロパティを変更する**btnPrivate**します。  
  
3.  ダブルクリックして、 **Say Goodbye**のイベント ハンドラーを追加するボタン、 **をクリックして**イベント。 イベントの手順で、次のコード行を配置します。  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  **ビルド**] メニューの [選択**BaseForm ライブラリのビルド**クラス ライブラリをビルドします。  
  
     ライブラリがビルドされたら、作成したフォームから継承する新しいプロジェクトを作成できます。  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>基本フォームから継承したフォームを含むプロジェクトを作成するには  
  
1.  **ファイル** メニューの 選択**追加**し**新しいプロジェクト**を開く、**新しいプロジェクトの追加** ダイアログ ボックス。  
  
2.  という名前の Windows フォーム アプリケーションを作成する`InheritanceTest`します。  
  
#### <a name="to-add-an-inherited-form"></a>継承されたフォームを追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**プロジェクトで、**追加**、し、**新しい項目の**します。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、 **Windows フォーム**カテゴリ (カテゴリの一覧の場合) と選択し、**継承されたフォーム**テンプレート。  
  
3.  既定の名前をそのまま`Form2`し**追加**します。  
  
4.  **継承ピッカー**ダイアログ ボックスで、 **Form1**から、 **BaseFormLibrary**フォームから継承し、をクリックするとプロジェクト**OK**.  
  
     これでフォームを作成、 **InheritanceTest**プロジェクト内のフォームから派生した**BaseFormLibrary**します。  
  
5.  継承されたフォームを開きます (**Form2**) がまだ開いていない場合をダブルクリックしてデザイナーでします。  
  
     デザイナーで、継承されたボタンがある記号 (![VisualBasicInheritanceSymbol screenshot](./media/vbinheritanceglyph.gif "vbInheritanceGlyph")) 継承されることを示す、隅。  
  
6.  選択、 **Say こんにちは**ボタンをクリックし、サイズ変更ハンドルを観察します。 このボタンは保護されているため、継承元が、移動、サイズ変更、キャプションの変更、およびその他の変更を実行できます。  
  
7.  プライベート**Say Goodbye**ボタン、およびサイズ変更ハンドルがないことに注意してください。 さらに、**プロパティ**を変更できないことを示すために、このボタンのプロパティ ウィンドウが淡色表示されています。  
  
8.  Visual c#: 使用している場合  
  
    1.  **ソリューション エクスプ ローラー**、右クリックして**Form1**で、 **InheritanceTest**プロジェクト**削除**します。 メッセージ ボックスが表示されますが、次のようにクリックします。 **OK** 、削除を確定します。  
  
    2.  Program.cs ファイルを開き、行 `Application.Run(new Form1());` を `Application.Run(new Form2());` に変更します。  
  
9. **ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**順に選択して**スタートアップ プロジェクトとして設定**します。  
  
10. **ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**順に選択して**プロパティ**します。  
  
11. **InheritanceTest**プロパティ ページ、設定、**スタートアップ オブジェクト**継承されたフォーム (**Form2**)。  
  
12. F5 を押してアプリケーションを実行し、継承されたフォームの動作を確認します。  
  
## <a name="next-steps"></a>次の手順  
 ユーザー コントロールの継承はほぼ同じ方法で機能します。 新しいクラス ライブラリ プロジェクトを開き、ユーザー コントロールを追加します。 内在コントロールを配置し、プロジェクトをコンパイルします。 別の新しいクラス ライブラリ プロジェクトを開き、コンパイル済みのクラス ライブラリへの参照を追加します。 また、[継承コントロールを追加してみてください (を通じて、**新しい項目の追加**] ダイアログ ボックス) をプロジェクトを使用して、**継承ピッカー**します。 ユーザー コントロールを追加し、変更、 `Inherits` (`:` Visual c#) ステートメント。 詳細については、「[方法 :Windows フォームを継承する](how-to-inherit-windows-forms.md)します。  
  
## <a name="see-also"></a>関連項目
- [方法: Windows フォームを継承します。](how-to-inherit-windows-forms.md)
- [Windows フォームのビジュアルの継承](windows-forms-visual-inheritance.md)
- [Windows フォーム](../index.md)

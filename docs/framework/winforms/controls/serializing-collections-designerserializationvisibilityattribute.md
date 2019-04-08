---
title: 'チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
ms.openlocfilehash: 04eb56fe78aa2d9ef5ab0daae4ba1c873cfc2b26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097760"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化
カスタム コントロールでは、プロパティとしてコレクションを公開が場合があります。 このチュートリアルを使用する方法について説明、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>デザイン時にコレクションをシリアル化する方法を制御するクラス。 適用、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>値をコレクション プロパティにより、プロパティをシリアル化されます。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法:Designerserializationvisibilityattribute を使用、基本データ型のコレクションをシリアル化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>シリアル化可能なコレクションを持つコントロールを作成します。  
 最初の手順では、プロパティとしてシリアル化可能なコレクションを持つコントロールを作成します。 使用してこのコレクションの内容を編集することができます、**コレクション エディター**からアクセスできますが、**プロパティ**ウィンドウ。  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>シリアル化可能なコレクションを使用してコントロールを作成するには  
  
1.  という名前の Windows コントロール ライブラリ プロジェクトを作成する`SerializationDemoControlLib`します。 詳細については、次を参照してください。 [Windows コントロール ライブラリ テンプレート](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))します。  
  
2.  名前を変更`UserControl1`に`SerializationDemoControl`します。 詳細については、次を参照してください。[コード シンボルのリファクタリングの名前を変更](/visualstudio/ide/reference/rename)します。  
  
3.  **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType>プロパティを`10`します。  
  
4.  場所、<xref:System.Windows.Forms.TextBox>を制御、`SerializationDemoControl`します。  
  
5.  <xref:System.Windows.Forms.TextBox> コントロールを選択します。 **プロパティ**ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|変更後の値|  
    |--------------|---------------|  
    |**Multiline**|`true`|  
    |**ドッキング**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**ReadOnly**|`true`|  
  
6.  **コード エディター**、という名前の文字列配列フィールドを宣言`stringsValue`で`SerializationDemoControl`します。  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  定義、`Strings`プロパティを`SerializationDemoControl`します。  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>値を使用して、コレクションのシリアル化を有効にします。  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。  
  
2.  検索、`Strings`プロパティ、<xref:System.Windows.Forms.PropertyGrid>の**UserControl Test Container**します。 をクリックして、`Strings`プロパティ、省略記号をクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタンをクリックする、 **の文字列コレクションエディター**.  
  
3.  内のいくつかの文字列を入力、**文字列コレクション エディター**します。 各文字列の最後に ENTER キーを押すで区切ります。 クリックして**OK**文字列の入力が完了したら。  
  
> [!NOTE]
>  入力した文字列に表示されます、<xref:System.Windows.Forms.TextBox>の`SerializationDemoControl`します。  
  
## <a name="serializing-a-collection-property"></a>コレクション プロパティをシリアル化します。  
 コントロールのシリアル化動作をテストするをフォームに配置を使用して、コレクションの内容を変更するが、**コレクション エディター**します。 特殊なデザイナー ファイルを調べることで、シリアル化されたコレクションの状態を確認できます、 **Windows フォーム デザイナー**はコードを出力します。  
  
#### <a name="to-serialize-a-collection"></a>コレクションをシリアル化するには  
  
1.  Windows アプリケーション プロジェクトをソリューションに追加します。 プロジェクトに `SerializationDemoControlTest` という名前を付けます。  
  
2.  **ツールボックス**、という名前のタブを見つける**SerializationDemoControlLib コンポーネント**します。 このタブでは紹介、`SerializationDemoControl`します。 詳細については、「[チュートリアル:カスタム コンポーネントでツールボックスが自動的に入力](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)します。  
  
3.  場所、`SerializationDemoControl`フォームにします。  
  
4.  検索、`Strings`プロパティ、**プロパティ**ウィンドウ。 をクリックして、`Strings`プロパティ、省略記号をクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタンをクリックする、 **の文字列コレクションエディター**.  
  
5.  内のいくつかの文字列を入力、**文字列コレクション エディター**します。 各文字列の最後に ENTER キーを押すで区切ります。 クリックして**OK**文字列の入力が完了したら。  
  
> [!NOTE]
>  入力した文字列に表示されます、<xref:System.Windows.Forms.TextBox>の`SerializationDemoControl`します。  
  
1.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。  
  
2.  開く、 **Form1**ノード。 という名前のファイルは、その下に**Form1.Designer.cs**または**Form1.Designer.vb**します。 これは、ファイルに、 **Windows フォーム デザイナー**フォームとその子コントロールのデザイン時の状態を表すコードを出力します。 このファイルを**コード エディター**で開きます。  
  
3.  呼ばれる領域を開く**Windows フォーム デザイナーで生成されたコード**というラベルの付いたセクションを見つけて**serializationDemoControl1**します。 このラベルの下には、コントロールのシリアル化された状態を表すコードです。 代入に表示される手順 5. で入力した文字列、`Strings`プロパティ。 C# および Visual Basic では、次のコード例は、表示される内容の文字列"red"、「オレンジ」および「黄色」を入力したかどうかのようなコードを示します。  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  **コード エディター**の値を変更、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>上、`Strings`プロパティを<xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>します。  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. ソリューションを再構築、手順 3. および 4. を繰り返します。  
  
> [!NOTE]
>  ここで、 **Windows フォーム デザイナー**への割り当ては出力されません、`Strings`プロパティ。  
  
## <a name="next-steps"></a>次の手順  
 基本データ型のコレクションをシリアル化する方法を理解、デザイン時環境に、カスタム コントロールをより深く統合を検討してください。 次のトピックでは、カスタム コントロールのデザイン時の統合を強化する方法について説明します。  
  
-   [デザイン時アーキテクチャ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))  
  
-   [Windows フォーム コントロールの属性](attributes-in-windows-forms-controls.md)  
  
-   [デザイナーのシリアル化の概要](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))  
  
-   [チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [デザイナーのシリアル化の概要](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))
- [方法: Designerserializationvisibilityattribute を使用、基本データ型のコレクションをシリアル化します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
- [チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)

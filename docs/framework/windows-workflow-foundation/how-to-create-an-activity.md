---
title: '方法: アクティビティを作成します。'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 271f26888e8b140b64464f5c9c4eabb7170afe05
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709017"
---
# <a name="how-to-create-an-activity"></a>方法: アクティビティを作成します。

アクティビティは [!INCLUDE[wf1](../../../includes/wf1-md.md)] の動作の中心的な単位です。 アクティビティの実行ロジックはマネージ コードで実装できます。または他のアクティビティを使用して実装できます。 このトピックでは、2 つのアクティビティを作成する方法について説明します。 最初のアクティビティは、コードを使用してその実行ロジックを実装する単純なアクティビティです。 2 番目のアクティビティの実装は他のアクティビティを使用して定義されています。 これらのアクティビティは、チュートリアルの次の手順で使用します。

> [!NOTE]
> チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](https://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。

## <a name="create-the-activity-library-project"></a>アクティビティ ライブラリ プロジェクトを作成します。

1.  Visual Studio を開き、選択**新規** > **プロジェクト**から、**ファイル**メニュー。

2.  **新しいプロジェクト**ダイアログで、**インストール済み**カテゴリで、 **Visual c#** > **ワークフロー** (または**Visual Basic** > **ワークフロー**)。

    > [!NOTE]
    > 表示されない場合、**ワークフロー**テンプレートのカテゴリをインストールする必要があります、 **Windows Workflow Foundation** Visual Studio のコンポーネント。 選択、 **Visual Studio インストーラーを開く**の左側にあるリンク、**新しいプロジェクト**ダイアログ。 Visual Studio インストーラーでは、選択、**個々 のコンポーネント**タブ。その後、下、**開発アクティビティ**カテゴリを選択、 **Windows Workflow Foundation**コンポーネント。 選択**変更**コンポーネントをインストールします。

3. 選択、**アクティビティ ライブラリ**プロジェクト テンプレート。 型`NumberGuessWorkflowActivities`で、**名前**ボックスをクリックして**OK**します。

4.  右クリックして**Activity1.xaml**で**ソリューション エクスプ ローラー**選択**削除**します。 **[OK]** をクリックして確定します。

## <a name="create-the-readint-activity"></a>ReadInt アクティビティを作成します。

1.  選択**新しい項目の追加**から、**プロジェクト**メニュー。

2.  **インストール済み** > **一般的な項目**ノードの **ワークフロー**します。 選択**コード アクティビティ**から、**ワークフロー**一覧。

3.  型`ReadInt`に、**名前**ボックスをクリックして**追加**します。

4.  既存の `ReadInt` 定義を次の定義に置き換えます。

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt` アクティビティは、コード アクティビティ テンプレートの既定値である <xref:System.Activities.NativeActivity%601> ではなく <xref:System.Activities.CodeActivity> から派生します。 <xref:System.Activities.CodeActivity%601> は、<xref:System.Activities.Activity%601.Result%2A> 引数を介して公開される 1 つの結果がアクティビティによって提供される場合に使用できますが、<xref:System.Activities.CodeActivity%601> ではブックマークの使用がサポートされていないため、<xref:System.Activities.NativeActivity%601> が使用されます。

## <a name="create-the-prompt-activity"></a>Prompt アクティビティを作成します。

1.  キーを押して**Ctrl**+**Shift**+**B**プロジェクトをビルドします。 プロジェクトをビルドすると、このプロジェクトの `ReadInt` アクティビティを使用して、この手順からカスタム アクティビティをビルドできます。

2.  選択**新しい項目の追加**から、**プロジェクト**メニュー。

3.  **インストール済み** > **一般的な項目**ノードの **ワークフロー**します。 選択**アクティビティ**から、**ワークフロー**一覧。

4.  型`Prompt`に、**名前**ボックスをクリックして**追加**します。

5.  ダブルクリック**Prompt.xaml**で**ソリューション エクスプ ローラー**まだ表示されていない場合、デザイナーで表示します。

6.  クリックして**引数**を表示するアクティビティ デザイナーの左下で、**引数**ウィンドウ。

7.  クリックして**引数の作成**です。

8.  型`BookmarkName`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**文字列**から**引数の型**ドロップダウン リスト、およびキーを押します**Enter**引数を保存します。

9. クリックして**引数の作成**です。

10. 型`Result`に、**名前**新しく追加されたの下にあるボックス`BookmarkName`引数で、**アウト**から、**方向**ドロップダウン リストで、**Int32**から、**引数の型**ドロップダウン リスト、およびキーを押します**Enter**します。

11. クリックして**引数の作成**です。

12. 型`Text`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**文字列**から**引数の型**ドロップダウン リスト、およびキーを押します**Enter**引数を保存します。

     これら 3 つの引数は、次の手順で、<xref:System.Activities.Statements.WriteLine> アクティビティに追加される `ReadInt` アクティビティと `Prompt` アクティビティの対応する引数にバインドされます。

13. クリックして**引数**を閉じるアクティビティ デザイナーの左下で、**引数**ウィンドウ。

14. ドラッグ、**シーケンス**からのアクティビティ、**制御フロー**のセクション、**ツールボックス**にドロップし、**ここにアクティビティをドロップ**のラベル、**プロンプト**アクティビティ デザイナー。

    > [!TIP]
    > 場合、**ツールボックス**ウィンドウが表示されない場合、選択**ツールボックス**から、**ビュー**メニュー。

15. ドラッグ、 **WriteLine**からのアクティビティ、**プリミティブ**のセクション、**ツールボックス**にドロップし、**ここにアクティビティをドロップ**のラベル、**シーケンス**アクティビティ。

16. バインド、**テキスト**の引数、 **WriteLine**アクティビティを**テキスト**の引数、**プロンプト**」と入力してアクティビティ`Text`**c# 式を入力します**または**VB の式を入力します**ボックスに、**プロパティ**ウィンドウ、およびキーを押します、**タブ**。2 回のキー。 これで、IntelliSense リスト メンバー ウィンドウを閉じ、プロパティから選択を外してプロパティ値を保存します。 このプロパティは、」と入力して設定することもできます`Text`に、 **c# 式を入力します**または**VB の式を入力します。** ボックスに、アクティビティ自体。

    > [!TIP]
    > 場合、**プロパティ ウィンドウ**が表示されている、選択**プロパティ ウィンドウ**から、**ビュー**メニュー。

17. ドラッグ、 **ReadInt**からのアクティビティ、 **NumberGuessWorkflowActivities**のセクション、**ツールボックス**にドロップし、**シーケンス**アクティビティの後になるように、 **WriteLine**アクティビティ。

18. バインド、 **BookmarkName**の引数、 **ReadInt**アクティビティを**BookmarkName**の引数、**プロンプト** 」と入力してアクティビティ`BookmarkName`に、 **VB の式を入力します**の右側のボックスに、 **BookmarkName**引数、**プロパティ ウィンドウ**、し、キーを押します **。タブ**IntelliSense リスト メンバー ウィンドウを閉じるし、プロパティの保存を 2 回のキーします。

19. バインド、**結果**の引数、 **ReadInt**アクティビティを**結果**の引数、**プロンプト**」と入力してアクティビティ`Result`**VB の式を入力します**の右側のボックスに、**結果**の引数、**プロパティ ウィンドウ**、し、キーを押します、 **タブ。** 2 回のキーします。

20. キーを押して**Ctrl**+**Shift**+**B**ソリューションをビルドします。

## <a name="next-steps"></a>次の手順

これらのアクティビティを使用してワークフローを作成する方法については、チュートリアルでは、次の手順を参照してください[方法。ワークフロー作成](how-to-create-a-workflow.md)です。

## <a name="see-also"></a>関連項目

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [カスタム アクティビティの設計と実装](designing-and-implementing-custom-activities.md)
- [チュートリアル入門](getting-started-tutorial.md)
- [方法: ワークフローを作成します。](how-to-create-a-workflow.md)
- [カスタム アクティビティ デザイナーでの ExpressionTextBox の使用](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
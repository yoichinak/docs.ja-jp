---
title: 'チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 7509e2f5035cb05c20af379f9f6a141177d540d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127050"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する
非常に大量の表形式データを表示する場合、<xref:System.Windows.Forms.DataGridView>コントロールを設定できます、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティを`true`と明示的にそのデータ ストアと、コントロールの相互作用を管理します。 このような状況で、コントロールのパフォーマンスを微調整できます。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールがカスタム データ ストアとの対話を処理できるいくつかのイベントを提供します。 このチュートリアルでは、これらのイベント ハンドラーの実装プロセスを説明します。 このトピックのコード例では、わかりやすくするための非常に単純なデータ ソースを使用します。 実稼働設定で、キャッシュ内に表示され、処理する必要がある行のみを通常に読み込まれます<xref:System.Windows.Forms.DataGridView>と対話し、キャッシュを更新するイベントです。 詳細については、次を参照してください[Windows フォームの DataGridView コントロールで Just-In-Time データ読み込みで仮想モードの実装。](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法:仮想モードを実装で、Windows フォーム DataGridView コントロール](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-implement-virtual-mode"></a>仮想モードを実装するには  
  
1.  派生するクラスを作成<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
     次のコードには、いくつかの基本的な初期化が含まれています。 後の手順で使用されるいくつかの変数の宣言を提供しますが、`Main`メソッドとクラス コンス トラクターで単純なフォーム レイアウトを提供します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  フォームのハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>を制御し、サンプルの値を使用してデータ ストアを設定します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>データ ストアから要求されたセルの値を取得するイベントまたは`Customer`現在編集中のオブジェクト。  
  
     このイベントが発生したときに、<xref:System.Windows.Forms.DataGridView>コントロールがセルを描画する必要があります。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CellValuePushed>イベントで、編集セルの値を格納する、`Customer`編集された行を表すオブジェクト。 このイベントは、ユーザーがセル値の変更をコミットするたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.NewRowNeeded>新たに作成イベント`Customer`新しく作成された行を表すオブジェクト。  
  
     このイベントは、ユーザーが新しいレコードの行を入力するたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.RowValidated>イベントをデータ ストアに新しいまたは変更された行を保存します。  
  
     このイベントは、ユーザーが現在の行を変更するたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベントを示すかどうか、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>ユーザー編集モードで 2 回または 1 回は編集モードの外部では、esc キーを押して行の復帰を通知するときにイベントが発生します。  
  
     既定では、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>しない限り、現在の行にセルが変更されたときに、行の復帰時に発生します、<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>プロパティに設定されて`true`で、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベント ハンドラー。 このイベントは、コミットのスコープは実行時に決定する場合に便利です。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>の値を破棄するイベント、`Customer`現在の行を表すオブジェクト。  
  
     このイベントは、ユーザーが ESC キーを押して編集モードで 2 回または 1 回は編集モードの外部で行の復帰を通知するときに発生します。 現在の行にセルが修正されていない場合、または場合、このイベントは発生しませんの値、<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>プロパティに設定された`false`で、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベント ハンドラー。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.UserDeletingRow>既存を削除するイベント`Customer`オブジェクト データ ストアから、保存されていない破棄または`Customer`新しく作成された行を表すオブジェクト。  
  
     このイベントは、ユーザーが行ヘッダーをクリックして DEL キーを押して行を削除するたびに発生します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. 単純な実装`Customers`をこのコード例で使用されるデータ項目を表すクラス。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     表示されます、<xref:System.Windows.Forms.DataGridView>コントロールの 3 つの顧客レコードを格納します。 行の複数のセルの値を変更して 2 回編集モードの内外で 1 回編集モードを元の値の行全体を元に戻すには、esc キーを押します。 変更、追加、または、コントロール内の行を削除するときに`Customer`データ ストア内のオブジェクトの変更、追加、またはも削除します。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでの仮想モードを実装する必要がありますを処理するイベントの基本を理解、<xref:System.Windows.Forms.DataGridView>コントロール。 さまざまな方法でこの基本的なアプリケーションを改善することができます。  
  
-   外部データベースから値をキャッシュするデータ ストアを実装します。 キャッシュは、取得し、クライアント コンピューターの少量のメモリを消費しているときに表示するために必要なだけが含まれるように、必要に応じて値を破棄する必要があります。  
  
-   要件に応じて、データ ストアのパフォーマンスを微調整します。 たとえば、キャッシュ サイズを大きくして、データベース クエリの数を最小限に抑えることで、クライアント コンピューターのメモリ制限ではなく、低速回線接続の補正する可能性があります。  
  
 外部データベースから値をキャッシュの詳細については、次を参照してください。[方法。フォームの DataGridView コントロールの Windows でジャストイン タイムのデータ読み込みによる仮想モードの実装](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [方法: Windows フォーム DataGridView コントロールで仮想モードを実装する](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)

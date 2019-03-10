---
title: Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: 44c985cef035e33e88ba246584efcb30fe0e9b97
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705559"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装
仮想モードを実装する理由の 1 つ、<xref:System.Windows.Forms.DataGridView>コントロールは、必要な場合にのみデータを取得します。 これは呼び出されます*ジャストイン タイムのデータの読み込み*します。  
  
 リモート データベースで非常に大きなテーブルを使用する場合はなどを表示するために必要なデータのみを取得し、ユーザーのビューに新しい行をスクロールする場合にのみ、追加のデータを取得するスタートアップの遅延を回避するために必要する可能性があります。 アプリケーションを実行しているクライアント コンピューターの限られた量のデータを格納するために使用可能なメモリの場合は、データベースから新しい値を取得するときに使用されていないデータを破棄する場合がありますもします。  
  
 次のセクションでは、使用方法を説明します、<xref:System.Windows.Forms.DataGridView>ジャストイン タイムのキャッシュを制御します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法:フォームの DataGridView コントロールの Windows でジャストイン タイムのデータ読み込みによる仮想モードの実装](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)します。  
  
## <a name="the-form"></a>フォーム  
 次のコード例は、読み取り専用を含むフォームを定義します。<xref:System.Windows.Forms.DataGridView>とやり取りするコントロールを`Cache`オブジェクト、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>イベント ハンドラー。 `Cache`オブジェクトがローカルに保存された値を管理しを使用して、 `DataRetriever` Northwind サンプル データベースの Orders テーブルから値を取得するオブジェクト。 `DataRetriever`実装しているオブジェクト、`IDataPageRetriever`で必要なインターフェイス、`Cache`クラスは、初期化するためにも使用、<xref:System.Windows.Forms.DataGridView>行および列を制御します。  
  
 `IDataPageRetriever`、 `DataRetriever`、および`Cache`型はこのトピックの後半で説明します。  
  
> [!NOTE]
>  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>示しますインターフェイス  
 次のコード例を定義、`IDataPageRetriever`インターフェイスによって実装される、`DataRetriever`クラス。 このインターフェイスで宣言されている唯一の方法が、`SupplyPageOfData`メソッドは、最初の行インデックスおよびデータの 1 つのページ内の行の数が必要です。 これらの値は、データ ソースからデータのサブセットを取得する、実装者が使用されます。  
  
 A`Cache`オブジェクトは、データの最初の 2 つのページの読み込みに構築時にこのインターフェイスの実装を使用します。 キャッシュがこれらのページのいずれかを破棄しから値を含む新しいページを要求にキャッシュされていない値が必要に応じていつでも、`IDataPageRetriever`します。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever クラス  
 次のコード例を定義、`DataRetriever`クラスを実装、`IDataPageRetriever`サーバーからのデータ ページを取得するインターフェイス。 `DataRetriever`クラスも用意されています。`Columns`と`RowCount`プロパティを、<xref:System.Windows.Forms.DataGridView>ために必要な列を作成すると、適切な数の空の行を追加するコントロールを使用して、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション。 空の行を追加すると、テーブル内のすべてのデータが含まれている場合と同様に、コントロールできるように必要があります。 これは、スクロール バーのスクロール ボックスは、適切なサイズになり、ユーザーは、テーブルの任意の行にアクセスできることを意味します。 によって、行がいっぱいになる、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>ビューにスクロールする場合にのみ、イベント ハンドラー。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>キャッシュ クラス  
 次のコード例を定義、`Cache`クラスを介して作成されるデータの 2 つのページ、`IDataPageRetriever`実装します。 `Cache`クラス定義内部`DataPage`を含む構造を<xref:System.Data.DataTable>値を 1 つのキャッシュに格納するページと行のインデックスを作成する計算を表すページの上限と下限の境界。  
  
 `Cache`クラスは、構築時にデータの 2 つのページを読み込みます。 たびに、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>イベントは、値を要求、`Cache`オブジェクトかどうかを値が表示されます。 その 2 つのいずれかのページを、必要な場合は、を返します。 値が使用できないローカルで場合、`Cache`オブジェクトを調べ、その 2 つのページの惑星現在表示されている行がページし、返される要求の値を含む、新しいものに置き換えます。  
  
 データ ページ内の行の数は、画面に一度に表示できる行の数と同じが、このモデルは効率的に、最も最近表示したページに戻るには、テーブルのページング ユーザーをできます。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>その他の考慮事項  
 前のコード例は、ジャストイン タイム データの読み込みの例として提供されます。 効率を最大化を実現するために、独自のニーズのコードを変更する必要があります。 少なくともは、キャッシュ内のデータの 1 ページあたりの行の数の適切な値を選択する必要があります。 この値に渡される、`Cache`コンス トラクター。 1 ページあたりの行の数が同時に表示できる行の数以上する必要があります、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 最良の結果はパフォーマンス テストと使いやすさがシステムとユーザーの要件を決定するテストを実施する必要があります。 考慮する必要がありますをいくつかの要因には、アプリケーション、使用すると、ネットワーク接続の使用可能な帯域幅、および使用するサーバーの待機時間を実行しているクライアント コンピューターでメモリの量が含まれます。 帯域幅と待機時間は、ピーク時決定してください。  
  
 アプリケーションのスクロールのパフォーマンスを向上させるのには、ローカルに格納されているデータの量を変更できます。 起動時間を向上させるため、ただし、回避しなければならない大量のデータを最初に読み込みます。 変更することも、`Cache`クラスを格納できるデータ ページの数を増やしてください。 スクロールの効率を向上させる複数のデータ ページを使用することができますが、使用可能な帯域幅とサーバーの待機時間に応じて、データ ページ内の行の理想的な数を決定する必要があります。 サイズの小さいページでは、サーバーは、アクセス頻度の高いより短時間で要求されたデータを返します。 待機時間がより多くの帯域幅よりも問題の場合は、大規模なデータ ページを使用したい場合があります。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでの仮想モード](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [チュートリアル: Windows フォームの DataGridView コントロールで仮想モードの実装](implementing-virtual-mode-wf-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロールでジャストイン タイムのデータ読み込みによる仮想モードの実装](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

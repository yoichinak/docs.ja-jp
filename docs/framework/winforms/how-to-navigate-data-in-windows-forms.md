---
title: '方法: Windows フォームでデータ間を移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 2ba33f9ecb3a12a62c41af17d3f9ad6f6e3f8a5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801713"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>方法: Windows フォームでデータ間を移動する
Windows アプリケーションでは、データ ソース内のレコードをナビゲートする最も簡単な方法は、バインドする、<xref:System.Windows.Forms.BindingSource>コンポーネントをデータ ソースとし、バインド コントロールを<xref:System.Windows.Forms.BindingSource>します。 組み込みのナビゲーション メソッドを使用することができますし、<xref:System.Windows.Forms.BindingSource>このような<xref:System.Windows.Forms.BindingSource.MoveNext%2A>、 <xref:System.Windows.Forms.BindingSource.MoveLast%2A>、<xref:System.Windows.Forms.BindingSource.MovePrevious%2A>と<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>します。 これらのメソッドを使用して、調整は、<xref:System.Windows.Forms.BindingSource.Position%2A>と<xref:System.Windows.Forms.BindingSource.Current%2A>のプロパティ、<xref:System.Windows.Forms.BindingSource>適切にします。 項目を検索し、設定して、現在の項目として設定できる、<xref:System.Windows.Forms.BindingSource.Position%2A>プロパティ。  
  
### <a name="to-increment-the-position-in-a-data-source"></a>データ ソース内の位置をインクリメントするには  
  
1. 設定、<xref:System.Windows.Forms.BindingSource.Position%2A>のプロパティ、<xref:System.Windows.Forms.BindingSource>に進むにはレコードの位置に、バインドされたデータ。 次の例を使用して、<xref:System.Windows.Forms.BindingSource.MoveNext%2A>のメソッド、<xref:System.Windows.Forms.BindingSource>インクリメント、<xref:System.Windows.Forms.BindingSource.Position%2A>プロパティと、`nextButton`がクリックされました。 <xref:System.Windows.Forms.BindingSource>に関連付けられている、`Customers`データセットのテーブル`Northwind`します。  
  
    > [!NOTE]
    >  設定、<xref:System.Windows.Forms.BindingSource.Position%2A>最初または最後のレコードを超える値にプロパティにならないエラーとして、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]位置を一覧の境界外の値に設定することはできません。 最初と最後のレコードを経過したかどうかを知るためにアプリケーションで重要な場合は、データ要素の数を超えますかどうかをテストするロジックが含まれます。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>末尾または先頭が渡されるかどうかを確認するには  
  
1. <xref:System.Windows.Forms.BindingSource.PositionChanged> イベントのイベント ハンドラーを作成します。 ハンドラーでは、提案された位置の値が実際のデータ要素の数を超えたかどうかをテストできます。  
  
     次の例では、データの最後の要素に到達したかどうかをテストする方法を示します。 最後の要素でない場合は、例では、**次**フォーム上のボタンが無効になっています。  
  
    > [!NOTE]
    >  、コード内を移動する一覧を変更する必要があります再度有効にすることに注意してください、**次**ボタンをユーザーが新しいリストの全体の長さを表示可能性があります。 さらに、注意を上記<xref:System.Windows.Forms.BindingSource.PositionChanged>、特定のイベント<xref:System.Windows.Forms.BindingSource>に関連付けられて、イベント処理メソッドである必要がありますを使用します。 処理のためのメソッドの例を次に、<xref:System.Windows.Forms.BindingSource.PositionChanged>イベント。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>項目を検索し、現在の項目として設定するには  
  
1. 現在の項目として設定するレコードを検索します。 これを行うを使用して、<xref:System.Windows.Forms.BindingSource.Find%2A>のメソッド、<xref:System.Windows.Forms.BindingSource>場合は、データ ソースの実装、<xref:System.ComponentModel.IBindingList>します。 データの例をいくつかは実装するソース<xref:System.ComponentModel.IBindingList>は<xref:System.ComponentModel.BindingList%601>と<xref:System.Data.DataView>します。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [Windows フォームがサポートするデータ ソース](data-sources-supported-by-windows-forms.md)
- [Windows フォーム データ バインドの変更通知](change-notification-in-windows-forms-data-binding.md)
- [データ連結と Windows フォーム](data-binding-and-windows-forms.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)

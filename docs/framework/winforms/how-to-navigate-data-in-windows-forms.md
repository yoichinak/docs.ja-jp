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
ms.openlocfilehash: eb973497f51592b5d34c22e62da77612aec23c35
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964279"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>方法: Windows フォームでデータ間を移動する
Windows アプリケーションでは、データソース内のレコード間を移動する最も簡単な方法は、 <xref:System.Windows.Forms.BindingSource>コンポーネントをデータソースにバインドしてから、 <xref:System.Windows.Forms.BindingSource>コントロールをにバインドすることです。 その後、、 <xref:System.Windows.Forms.BindingSource> 、 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>および<xref:System.Windows.Forms.BindingSource.MoveNext%2A> <xref:System.Windows.Forms.BindingSource.MoveLast%2A>の組み込みナビゲーションメソッドを<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>使用できます。 これらのメソッドを使用する<xref:System.Windows.Forms.BindingSource.Position%2A>と<xref:System.Windows.Forms.BindingSource.Current%2A> 、 <xref:System.Windows.Forms.BindingSource>のプロパティとプロパティが適切に調整されます。 また、 <xref:System.Windows.Forms.BindingSource.Position%2A>プロパティを設定して、項目を検索し、現在の項目として設定することもできます。  
  
### <a name="to-increment-the-position-in-a-data-source"></a>データソース内の位置をインクリメントするには  
  
1. バインドされたデータ<xref:System.Windows.Forms.BindingSource>ののプロパティを、移動先のレコード位置に設定します。<xref:System.Windows.Forms.BindingSource.Position%2A> をクリックし<xref:System.Windows.Forms.BindingSource.MoveNext%2A>たとき`nextButton`に、 <xref:System.Windows.Forms.BindingSource>のメソッドを使用し<xref:System.Windows.Forms.BindingSource.Position%2A>てプロパティをインクリメントする例を次に示します。 は<xref:System.Windows.Forms.BindingSource> 、データ`Customers` セット`Northwind`のテーブルに関連付けられています。  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.Position%2A>このプロパティを最初または最後のレコードを超えた値に設定しても、エラーは発生しません。 .NET Framework では、リストの範囲外の値に位置を設定することができないためです。 最初または最後のレコードがなくなったかどうかを確認するためにアプリケーションで重要な場合は、データ要素数を超えるかどうかをテストするロジックを含めます。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>終了を超えたかどうかを確認するには  
  
1. <xref:System.Windows.Forms.BindingSource.PositionChanged> イベントのイベント ハンドラーを作成します。 ハンドラーでは、提案された位置の値が実際のデータ要素数を超えたかどうかをテストできます。  
  
     次の例は、最後のデータ要素に到達したかどうかをテストする方法を示しています。 この例では、最後の要素にある場合、フォームの **[次へ]** ボタンは無効になっています。  
  
    > [!NOTE]
    > コード内で移動するリストを変更する場合は、ユーザーが新しいリストの長さ全体を参照できるように、 **[次へ**] ボタンを再度有効にする必要があることに注意してください。 また、使用している特定<xref:System.Windows.Forms.BindingSource.PositionChanged> <xref:System.Windows.Forms.BindingSource>ののイベントがイベント処理メソッドに関連付けられている必要があることに注意してください。 <xref:System.Windows.Forms.BindingSource.PositionChanged>イベントを処理するメソッドの例を次に示します。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>項目を検索して現在の項目として設定するには  
  
1. 現在のアイテムとして設定するレコードを探します。 データソースが<xref:System.Windows.Forms.BindingSource.Find%2A> <xref:System.Windows.Forms.BindingSource>を実装<xref:System.ComponentModel.IBindingList>している場合は、のメソッドを使用してこれを行うことができます。 を実装<xref:System.ComponentModel.IBindingList>するデータソースの例とし<xref:System.Data.DataView>て、とが<xref:System.ComponentModel.BindingList%601>あります。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [Windows フォームがサポートするデータ ソース](data-sources-supported-by-windows-forms.md)
- [Windows フォーム データ バインドの変更通知](change-notification-in-windows-forms-data-binding.md)
- [データ連結と Windows フォーム](data-binding-and-windows-forms.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)

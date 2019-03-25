---
title: '方法: 複数のコントロールと同じデータ ソースにバインドが同期を維持'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: 01cec80c85beb64975648b2250c914fe04d3ac95
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721386"
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>方法: 複数のコントロールと同じデータ ソースにバインドが同期を維持
Windows フォームでのデータ バインディングを使用する場合に多くの場合は、複数のコントロールが、同じデータ ソースにバインドされます。 場合によっては、コントロールのバインドされたプロパティが相互およびデータ ソースとの同期を維持するために余分な手順を実行するために必要な場合があります。 次の手順では、2 つの状況で必要があります。  
  
-   データ ソースが実装していない場合<xref:System.ComponentModel.IBindingList>、して、生成<xref:System.ComponentModel.IBindingList.ListChanged>の種類のイベント<xref:System.ComponentModel.ListChangedType.ItemChanged>します。  
  
-   データ ソースの実装場合<xref:System.ComponentModel.IEditableObject>します。  
  
 前者の場合、使用することができます、<xref:System.Windows.Forms.BindingSource>データ ソースをコントロールにバインドします。 後者の場合でを使用して、<xref:System.Windows.Forms.BindingSource>を処理し、<xref:System.Windows.Forms.BindingSource.BindingComplete>イベントと呼び出し<xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A>、関連付けられている<xref:System.Windows.Forms.BindingManagerBase>します。  
  
## <a name="example"></a>例  
 次のコード例は、3 つのコントロールをバインドする方法を示します: 2 つのテキスト ボックス コントロールと<xref:System.Windows.Forms.DataGridView>コントロール-で同じ列に、<xref:System.Data.DataSet>を使用して、<xref:System.Windows.Forms.BindingSource>コンポーネント。 この例は、処理する方法を示します、<xref:System.Windows.Forms.BindingSource.BindingComplete>イベントを 1 つのテキスト ボックスのテキスト値が変更されたときに、追加のテキスト ボックスを確認してください、<xref:System.Windows.Forms.DataGridView>コントロールは、適切な値で更新されます。  
  
 この例では、<xref:System.Windows.Forms.BindingSource>データ ソースとコントロールをバインドします。 コントロールをデータ ソースに直接バインドを取得する代わりに、<xref:System.Windows.Forms.BindingManagerBase>から、フォームのバインドの<xref:System.Windows.Forms.Control.BindingContext%2A>し、処理、<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>イベントを<xref:System.Windows.Forms.BindingManagerBase>します。 これを行う方法の例は、ヘルプ ページをご覧ください。、<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>のイベント<xref:System.Windows.Forms.BindingManagerBase>します。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   このコード例が必要です。  
  
-   <xref:System>、<xref:System.Windows.Forms>、および <xref:System.Drawing> の各アセンブリへの参照。  
  
-   使用して、フォーム、<xref:System.Windows.Forms.Form.Load>イベントを処理済みとへの呼び出し、`InitializeControlsAndDataSource`メソッドから、フォームの例では<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目
- [方法: BindingSource コンポーネントを使用してフォーム間でバインド データを共有](./controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)
- [Windows フォーム データ バインドの変更通知](change-notification-in-windows-forms-data-binding.md)
- [データ連結に関連するインターフェイス](interfaces-related-to-data-binding.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)

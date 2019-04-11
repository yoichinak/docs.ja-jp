---
title: '方法: Windows フォームのコレクションにアクセス キーを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: fdd3a56ab9a267990bb0e832c0d4cc2af9334034
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214041"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>方法: Windows フォームのコレクションにアクセス キーを指定する
-   個々 のコレクション アイテムは、キーにアクセスできます。 この機能は Windows フォーム アプリケーションで通常使用される多くのコレクション クラスに追加されました。 キー付きコレクションがアクセス可能なコレクション クラスの一部を次に示します。  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 コレクション内の項目に関連付けられているキーは、通常、項目の名前です。 次の手順では、コレクション クラスを使用して一般的なタスクを実行する方法を示します。  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>コントロール コレクション内の入れ子になったコントロールにフォーカスを検索して  
  
-   使用して、<xref:System.Windows.Forms.Control.ControlCollection.Find%2A>と<xref:System.Windows.Forms.Control.Focus%2A>メソッドを検索し、フォーカスをコントロールの名前を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>イメージ コレクション内のイメージにアクセスするには  
  
-   使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>プロパティにアクセスするイメージの名前を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>タブ ページを選択したタブとして設定するには  
  
-   使用して、<xref:System.Windows.Forms.TabControl.SelectedTab%2A>プロパティと共に、<xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>プロパティを選択したタブとして設定するタブ ページの名前を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [Windows フォームについて](getting-started-with-windows-forms.md)
- [方法: Windows フォームの ImageList コンポーネントにイメージを追加または削除する](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)

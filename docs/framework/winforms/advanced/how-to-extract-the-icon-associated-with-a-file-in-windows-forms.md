---
title: '方法: Windows フォームでファイルに関連付けられているアイコンを抽出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: d754dc5e8a57b3c4e2e5439bb2524a22d44813c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112555"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>方法: Windows フォームでファイルに関連付けられているアイコンを抽出する
多数のファイルには、関連付けられているファイルの種類のビジュアル表現を提供するアイコンが埋め込まれています。 たとえば、Microsoft Word ドキュメントには、それらを Word 文書として識別するアイコンが含まれます。 リスト コントロールにテーブル コントロール ファイルを表示するときに各ファイル名の横にあるファイルの種類を表すアイコンを表示したい場合があります。 使用して簡単に行うことができます、<xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>メソッド。  
  
## <a name="example"></a>例  
 次のコード例は、ファイルに関連付けられたアイコンを抽出し、ファイル名と関連付けられているアイコンで表示する方法を示します、<xref:System.Windows.Forms.ListView>コントロール。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 例をコンパイルするには。  
  
-   Windows フォーム、および呼び出しに上記のコードを貼り付け、`ExtractAssociatedIconExample`フォームのコンス トラクターからメソッドまたは<xref:System.Windows.Forms.Form.Load>イベント処理メソッド。  
  
     フォームをインポートすることを確認する必要があります、<xref:System.IO>名前空間。  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [ListView コントロール](../controls/listview-control-windows-forms.md)

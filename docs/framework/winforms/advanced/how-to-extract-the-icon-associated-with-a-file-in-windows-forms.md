---
title: '方法: Windows フォームでファイルに関連付けられているアイコンを抽出します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 5cbce48643d21418d580a6db44f86b00cf50fb9d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714191"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>方法: Windows フォームでファイルに関連付けられているアイコンを抽出します。
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

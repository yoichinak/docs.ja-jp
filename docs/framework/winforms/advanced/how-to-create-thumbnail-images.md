---
title: '方法: サムネイル イメージを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: b9afbac85dee90938e2bd55ebe19d3b02c0d66d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341492"
---
# <a name="how-to-create-thumbnail-images"></a>方法: サムネイル イメージを作成する
サムネイル イメージは、小さいイメージのバージョンです。 サムネイル イメージを作成するには呼び出すことによって、<xref:System.Drawing.Image.GetThumbnailImage%2A>のメソッド、<xref:System.Drawing.Image>オブジェクト。  
  
## <a name="example"></a>例  
 次の例では、構築、 <xref:System.Drawing.Image> JPG ファイルからのオブジェクト。 元のイメージは、640 ピクセルの幅および 479 ピクセルの高さを持ちます。 コードでは、100 ピクセルの幅と高さ 100 ピクセルの持つサムネイル イメージを作成します。  
  
 次の図は、サムネイル画像を示します。  
  
 ![サムネイル画像](./media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  この例では、コールバック メソッドが宣言されるが、使用されていません。 これには、GDI + のすべてのバージョンがサポートしています。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 例を実行するには、次の手順に従います。  
  
1. 新しい Windows フォーム アプリケーションを作成します。  
  
2. コード例をフォームに追加します。  
  
3. フォームのハンドラーを作成<xref:System.Windows.Forms.Control.Paint>イベント  
  
4. <xref:System.Windows.Forms.Control.Paint>ハンドラーを呼び出し、`GetThumbnail`メソッドを渡します`e`の<xref:System.Windows.Forms.PaintEventArgs>します。  
  
5. サムネイルを作成したいイメージ ファイルを検索します。  
  
6. `GetThumbnail`メソッドは、パスを指定し、ファイル名をイメージにします。  
  
7. F5 キーを押して、例を実行します。  
  
     フォームに 100 × 100 のサムネイル画像が表示されます。  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)

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
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923752"
---
# <a name="how-to-create-thumbnail-images"></a>方法: サムネイル イメージを作成する
サムネイル画像は、イメージの小さなバージョンです。 オブジェクトのメソッド<xref:System.Drawing.Image.GetThumbnailImage%2A>を呼び出すことにより、サムネイルイメージを作成できます。 <xref:System.Drawing.Image>  
  
## <a name="example"></a>例  
 次の例では<xref:System.Drawing.Image> 、JPG ファイルからオブジェクトを構築します。 元のイメージの幅は640ピクセル、高さは479ピクセルです。 このコードでは、幅100ピクセル、高さ100ピクセルのサムネイル画像を作成します。  
  
 サムネイル画像を次の図に示します。  
  
 ![出力サムネイルを示すスクリーンショット。](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> この例では、コールバックメソッドが宣言されていますが、使用されていません。 これは、GDI + のすべてのバージョンをサポートします。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 この例を実行するには、次の手順に従います。  
  
1. 新しい Windows フォーム アプリケーションを作成します。  
  
2. サンプルコードをフォームに追加します。  
  
3. フォームの<xref:System.Windows.Forms.Control.Paint>イベントのハンドラーを作成します。  
  
4. ハンドラーで、 `GetThumbnail`メソッドを呼び出し、にを`e` <xref:System.Windows.Forms.PaintEventArgs>渡します。 <xref:System.Windows.Forms.Control.Paint>  
  
5. サムネイルを作成するイメージファイルを検索します。  
  
6. `GetThumbnail`メソッドで、イメージのパスとファイル名を指定します。  
  
7. F5 キーを押して、例を実行します。  
  
     100の100サムネイル画像がフォームに表示されます。  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)

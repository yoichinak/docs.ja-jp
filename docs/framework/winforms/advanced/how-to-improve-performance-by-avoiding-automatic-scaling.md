---
title: '方法: 自動スケーリングを解除してパフォーマンスを向上させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
ms.openlocfilehash: b8238a4f0ce482d63ab33833c4bceaaa2814253d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705340"
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>方法: 自動スケーリングを解除してパフォーマンスを向上させる
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 描画すると、パフォーマンスが低下する、イメージをスケーリング自動的に場合があります。 描画先の四角形の大きさを渡すことによって、イメージのスケーリングを制御する代わりに、<xref:System.Drawing.Graphics.DrawImage%2A>メソッド。  
  
 たとえば、次の呼び出し、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドの左上隅を指定します (50, 30) 先の四角形が指定されていません。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 これは最も簡単なバージョンのですが、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドで必須の引数の数の観点からは最も効率的とは限りません。 解像度がで使用される場合[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)](通常は 96 ドット/インチ) に格納されている解像度とは異なる、<xref:System.Drawing.Image>オブジェクト、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは、イメージを拡大縮小されます。 たとえば、<xref:System.Drawing.Image>オブジェクト 216 ピクセルの幅とのインチあたりのドット数 72 ストアド水平方向の解像度の値があります。 216/72 が 3、ため<xref:System.Drawing.Graphics.DrawImage%2A>を 1 インチあたり 96 ドットの解像度で 3 インチの幅を持つようにイメージをスケーリングします。 つまり、<xref:System.Drawing.Graphics.DrawImage%2A>が 96 x 3 = 288 の幅を持つイメージが表示されます (ピクセル)。  
  
 画面の解像度が 1 インチあたり 96 ドットと異なる場合でも[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]はおそらくスケール イメージ画面の解像度が 96 ドット/インチであるかのようです。 だ、 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics>オブジェクトは、デバイス コンテキストに関連付けられてとタイミング[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]結果画面の解像度のデバイス コンテキストは、実際の画面の解像度に関係なく、96 では、通常のクエリ。 先の四角形を指定することで自動スケーリングを避けることができます、<xref:System.Drawing.Graphics.DrawImage%2A>メソッド。  
  
## <a name="example"></a>例  
 次の例では、2 回、同じイメージを描画します。 最初のケースでは、先の四角形の高さと幅が指定されていないと、イメージが自動的に拡大/縮小します。 2 番目のケースではの幅と高さ (ピクセル単位で測定) 先の四角形は、幅と、元のイメージの高さと同じであることを指定します。 次の図は、2 回表示されるイメージを示します。  
  
 ![スケール テクスチャ](./media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 Texture.jpg をイメージの名前と、システムで有効なパスに置き換えます。  
  
## <a name="see-also"></a>関連項目
- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)

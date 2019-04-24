---
title: '方法: カラー行列を使用して単一色を変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 78fc498b0689026fb74ec0c422948c1879495560
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342857"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>方法: カラー行列を使用して単一色を変換する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>クラスを格納すると、画像を操作します。 <xref:System.Drawing.Image> <xref:System.Drawing.Bitmap>オブジェクトは、32 ビットの数値として各ピクセルの色を格納します。8 ビットは赤、緑、青、およびアルファの各します。 4 つのコンポーネントのそれぞれは、0 ~ 255 の輝度がない、255 は最大輝度を表す 0 から番号です。 アルファ コンポーネントには、色の透明度を指定します。0 は完全に透明、255 は完全に不透明です。  
  
 カラー ベクターは、(赤、緑、青、アルファ) 形式の 4 タプルです。 たとえば、色のベクトル (0, 255、0, 255) は、不透明な色が赤と青、緑を最大輝度にあるを表します。  
  
 色を表すための別の規則は、最大輝度を番号 1 を使用します。 その規則を使用して、前の段落で説明されている色は、ベクトル (0, 1、0, 1) によって示されます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 色変換を実行するときに、最大輝度として 1 の規則を使用します。  
  
 4 × 4 行列によって色ベクトルを乗算して、色のベクトルに線形変換 (回転、スケーリング、およびなど) を適用できます。 ただし、4 × 4 行列を使用して、(非線形) 変換を実行することはできません。 各色ベクター ダミー 5 番目の座標 (たとえば、番号 1) を追加する場合は、線形変換と翻訳の任意の組み合わせを適用する 5 × 5 マトリックスを使用できます。 変換後に線形変換から成る変換アフィン変換と呼びます。  
  
 たとえば、色 (0.2, 0.0、0.4, 1.0) で起動して、次の変換を適用するとします。  
  
1. 赤のコンポーネントでは倍精度浮動小数点  
  
2. 0.2 を赤、緑、青のコンポーネントに追加します。  
  
 次の行列の乗算を順番に、2 つの変換を実行します。  
  
 ![色の変更](./media/recoloring01.gif "recoloring01")  
  
 カラー行列の要素は、行と列 (0 から始まる) インデックス付けられます。 たとえば、5 行目と 3 番目の列の行列 M のエントリは、M [4] [2] で表されます。  
  
 (次の図に示すように) 5 つ × 5 単位行列では、対角線上の 1 と 0 それ以外の場所が。 恒等行列によって色ベクトルを乗算する場合、色のベクターは変更されません。 色変換の行列を形成する便利な方法では、恒等行列で開始し、必要な変換を生成する少し変更します。  
  
 ![色の変更](./media/recoloring02.gif "recoloring02")  
  
 マトリックスと変換の詳細については、次を参照してください。[座標系と変換](coordinate-systems-and-transformations.md)します。  
  
## <a name="example"></a>例  
 次の例は、イメージを 1 つのすべての色 (0.2, 0.0、0.4, 1.0) は、前の段落で説明されている変換を適用します。  
  
 次の図は、右側の左側に、元のイメージと変換後のイメージを示します。  
  
 ![色](./media/colortrans1.png "colortrans1")  
  
 次の例のコードでは、次の手順を使用して、色の変更を実行します。  
  
1. 初期化を<xref:System.Drawing.Imaging.ColorMatrix>オブジェクト。  
  
2. 作成、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクトを渡します、<xref:System.Drawing.Imaging.ColorMatrix>オブジェクトを<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>のメソッド、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクト。  
  
3. 渡す、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッドを<xref:System.Drawing.Graphics>オブジェクト。  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- [イメージの色の変更](recoloring-images.md)
- [座標系と変換](coordinate-systems-and-transformations.md)

---
title: 座標系の種類
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: 765df4bcd3cef83e624ad8b11676696b95f7d035
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792368"
---
# <a name="types-of-coordinate-systems"></a>座標系の種類
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 次の 3 つの座標空間を使用して: 世界、ページ、およびデバイス。 ワールド座標は特定のグラフィック ワールドをモデル化するために使用する座標は、.NET Framework のメソッドに渡す座標です。 ページ座標は、フォームやコントロールなどの描画サーフェイスで使用される座標系を参照してください。 デバイス座標は、画面や紙など、描画されている物理デバイスで使用される座標です。 呼び出しを行うとき`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`、ポイントに渡す、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド:`(0, 0)`と`(160, 80)`: ワールド座標空間では。 前に[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]画面に、直線を描画することができます、座標変換のシーケンスを通過します。 ワールド変換と呼ばれる 1 つの変換は、ページ座標にワールド座標を変換し、ページの変換と呼ばれる別の変換は、ページ座標をデバイス座標に変換します。  
  
## <a name="transforms-and-coordinate-systems"></a>座標系と変換  
 左上隅ではなく、クライアント領域の本体でに原点がある座標系を使用するとします。 たとえば、クライアント領域の上部から 50 ピクセルとクライアント領域の左端から 100 ピクセルにする配信元にするとします。 次の図は、このような座標系を示します。  
  
 ![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 呼び出しを行うとき`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`、次の図に示すように行を取得します。  
  
 ![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 次の 3 つの座標空間で、行の端点の座標は次のとおりです。  
  
|||  
|-|-|  
|World|(0, 0) に (160, 80)|  
|ページ|(100, 50) を (260、130)|  
|デバイス|(100, 50) を (260、130)|  
  
 ページ座標空間がクライアント領域の左上隅にある原点を持つことに注意してください。これは、大文字と小文字を常になります。 測定単位がピクセルであるため、デバイス座標がページ座標と同じにも注意してください。 測定単位をピクセル (たとえば、インチ) 以外に設定した場合は、デバイス座標がページ座標から別になります。  
  
 ワールド座標をマップ ページ座標、ワールド変換に保持されている、<xref:System.Drawing.Graphics.Transform%2A>のプロパティ、<xref:System.Drawing.Graphics>クラス。 前の例では、ワールド変換は x 方向に翻訳 100 単位と y 軸方向で 50 ユニット。 次の例のワールド変換の設定、<xref:System.Drawing.Graphics>オブジェクトを使用して<xref:System.Drawing.Graphics>上記の図に示すように行を描画するオブジェクト。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 ページの変換は、デバイス座標にページ座標をマップします。 <xref:System.Drawing.Graphics>クラスには、<xref:System.Drawing.Graphics.PageUnit%2A>と<xref:System.Drawing.Graphics.PageScale%2A>ページ変換を操作するためのプロパティ。 <xref:System.Drawing.Graphics>クラスでは、2 つの読み取り専用のプロパティも提供します<xref:System.Drawing.Graphics.DpiX%2A>と<xref:System.Drawing.Graphics.DpiY%2A>、ディスプレイ デバイスの 1 インチあたりのドット数水平および垂直方向を確認するためです。  
  
 使用することができます、<xref:System.Drawing.Graphics.PageUnit%2A>のプロパティ、<xref:System.Drawing.Graphics>ピクセル以外のメジャーの単位を指定するクラス。  
  
> [!NOTE]
>  設定することはできません、<xref:System.Drawing.Graphics.PageUnit%2A>プロパティを<xref:System.Drawing.GraphicsUnit.World>をこの物理単位でないし、例外が発生します。  
  
 次の例から線を描画します (0, 0) に (2, 1)、ここ 2 インチ右側に、点 (0, 0) からダウン 1 インチは、ポイント (2, 1)。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  ペンの幅を指定しないのは、ペンを構築するときに、前の例は 1 インチ幅の線を描画します。 ペンの幅を指定するには、2 番目の引数で、<xref:System.Drawing.Pen>コンス トラクター。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 ディスプレイ デバイスが 96 ドット/インチで水平方向と垂直方向の 1 インチあたり 96 ドットであると、想定した場合、3 つの座標空間に次座標がある前の例では行のエンドポイント。  
  
|||  
|-|-|  
|World|(0, 0) に (2, 1)|  
|ページ|(0, 0) に (2, 1)|  
|デバイス|(0, 0, に (192, 96)|  
  
 ワールド座標の原点がクライアント領域の左上隅にあるため、ページ座標がワールド座標と同じに注意してください。  
  
 さまざまな効果を実現するために世界とページの変換を組み合わせることができます。 たとえば、メジャーの単位として (インチ) を使用して、クライアント領域の上端からの 1/2 インチ、クライアント領域の左端から 2 インチ、座標系の原点します。 次の例の世界とページの変換の設定、<xref:System.Drawing.Graphics>オブジェクトし、後から線を描画します (0, 0) に (2, 1)。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 次の図は、行と座標系を示します。  
  
 ![座標系](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 ディスプレイ デバイスが 96 ドット/インチで水平方向と垂直方向の 1 インチあたり 96 ドットであると、想定した場合、3 つの座標空間に次座標がある前の例では行のエンドポイント。  
  
|||  
|-|-|  
|World|(0, 0) に (2, 1)|  
|ページ|(2, 0.5) に (4, 1.5)|  
|デバイス|(192, 48) に (384、144)|  
  
## <a name="see-also"></a>関連項目

- [座標系と変換](coordinate-systems-and-transformations.md)
- [変換の行列表現](matrix-representation-of-transformations.md)

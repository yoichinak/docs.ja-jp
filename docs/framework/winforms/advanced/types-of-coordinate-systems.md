---
title: "座標系の種類"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287b1c9eddef882041d9e4eac44a06190f3585a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="types-of-coordinate-systems"></a>座標系の種類
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]次の 3 つの座標空間を使用して: world、ページ、およびデバイス。 ワールド座標特定グラフィック世界をモデル化するために使用する座標、.NET Framework のメソッドに渡す座標。 ページ座標は、フォームやコントロールなどの描画サーフェイスで使用される座標系を参照してください。 デバイスの座標は、画面や枚の用紙など、描画されている物理デバイスで使用される座標です。 呼び出しを行うとき`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`、渡された点、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド —`(0, 0)`と`(160, 80)`— 世界の座標空間にします。 前に[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]画面に線を描画することができます、座標は、変換のシーケンスを通過します。 ワールド変換と呼ばれる 1 つの変換は、ページ座標にワールド座標を変換し、ページ変換と呼ばれる別の変換は、ページ座標をデバイス座標に変換します。  
  
## <a name="transforms-and-coordinate-systems"></a>座標系と変換  
 左上隅ではなく、クライアント領域の本体の原点をある座標システムを使用するとします。 たとえば、原点とするクライアント領域の上部から 50 ピクセルとクライアント領域の左端から 100 ピクセルにすることです。 次の図は、このような座標系を示します。  
  
 ![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 呼び出しを行うとき`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`、次の図に示すように行を取得します。  
  
 ![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 3 つの座標空間、行の端点の座標は次のとおりです。  
  
|||  
|-|-|  
|世界|(0, 0) に (160、80)|  
|ページ|(100, 50) に (260、130)|  
|デバイス|(100, 50) に (260、130)|  
  
 ページの座標空間にあるクライアント領域の左上隅に原点に注意してください。これは、大文字と小文字を常になります。 測定単位はピクセルであるため、デバイス座標があるページ座標と同じにも注意してください。 ピクセル (たとえば、インチ) 以外に測定単位を設定した場合、デバイスの座標はページ座標から異なるされます。  
  
 ワールド変換は、ページ座標にワールド座標をマップに保持されている、<xref:System.Drawing.Graphics.Transform%2A>のプロパティ、<xref:System.Drawing.Graphics>クラスです。 前の例では、ワールド変換は、x 軸方向の平行移動 100 単位および y 方向の 50 個のユニットです。 次の例のワールド変換の設定、<xref:System.Drawing.Graphics>オブジェクトを使用している<xref:System.Drawing.Graphics>前の図に示すように線を描画するオブジェクト。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 ページ変換は、デバイスの座標にページ座標をマップします。 <xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.PageUnit%2A>と<xref:System.Drawing.Graphics.PageScale%2A>ページ変換を操作するためのプロパティです。 <xref:System.Drawing.Graphics>クラスは、2 つの読み取り専用のプロパティも用意されています。<xref:System.Drawing.Graphics.DpiX%2A>と<xref:System.Drawing.Graphics.DpiY%2A>、ディスプレイ デバイスのインチあたりのドット数水平および垂直方向を確認するためです。  
  
 使用することができます、<xref:System.Drawing.Graphics.PageUnit%2A>のプロパティ、<xref:System.Drawing.Graphics>ピクセル以外のメジャーの単位を指定するクラス。  
  
> [!NOTE]
>  設定することはできません、<xref:System.Drawing.Graphics.PageUnit%2A>プロパティを<xref:System.Drawing.GraphicsUnit.World>、物理的な単位ではないになり、例外が発生します。  
  
 次の例から行を描画する (0, 0) に (2, 1)、場所、ポイント (2, 1) が 2 インチ右側に、ポイント (0, 0) から 1 インチ下。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  ペンを構築するときに、ペンの幅を指定しない、前の例は 1 インチの線を描画します。 2 番目の引数でペンの幅を指定できます、<xref:System.Drawing.Pen>コンス トラクター。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 仮定すると、表示デバイスが 96 ドット/インチで水平方向および垂直方向のインチあたりのドット数 96 を持っている、前の例では行の端点座標にある、次は 3 つの座標空間内。  
  
|||  
|-|-|  
|世界|(0, 0) に (2, 1)|  
|ページ|(0, 0) に (2, 1)|  
|デバイス|(0, 0, に (192、96)|  
  
 世界の座標空間の原点がクライアント領域の左上隅にあるため、ページ座標は、世界の座標と同じに注意してください。  
  
 さまざまな効果を実現するために、world とページ変換を組み合わせることができます。 たとえば、メジャーの単位として (インチ) を使用して、クライアント領域とクライアント領域の上端からの 1/2 インチの左端からの 2 インチ、座標系の原点です。 次の例は、ワールド変換とページ変換の<xref:System.Drawing.Graphics>オブジェクトおよびから線を描画し、(0, 0) に (2, 1)。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 次の図は、行と座標系を示します。  
  
 ![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 仮定すると、表示デバイスが 96 ドット/インチで水平方向および垂直方向のインチあたりのドット数 96 を持っている、前の例では行の端点座標にある、次は 3 つの座標空間内。  
  
|||  
|-|-|  
|世界|(0, 0) に (2, 1)|  
|ページ|(2, 0.5) に (4, 1.5)|  
|デバイス|(192, 48) に (384, 144)|  
  
## <a name="see-also"></a>参照  
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [変換の行列表現](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)

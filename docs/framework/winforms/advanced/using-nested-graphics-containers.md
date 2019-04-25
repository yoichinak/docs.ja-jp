---
title: 入れ子になっているグラフィックス コンテナーの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: 6bbf7918ccff184e597204b35aa005ab17d8d8af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104300"
---
# <a name="using-nested-graphics-containers"></a>入れ子になっているグラフィックス コンテナーの使用
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 置換またはで状態の一部を強化を一時的に使用できるコンテナーを提供します、<xref:System.Drawing.Graphics>オブジェクト。 呼び出すことでコンテナーを作成する、<xref:System.Drawing.Graphics.BeginContainer%2A>のメソッドを<xref:System.Drawing.Graphics>オブジェクト。 呼び出すことができます<xref:System.Drawing.Graphics.BeginContainer%2A>繰り返しを入れ子になったコンテナーを形成します。 呼び出しごとに<xref:System.Drawing.Graphics.BeginContainer%2A>への呼び出しと組み合わせて使用する必要があります<xref:System.Drawing.Graphics.EndContainer%2A>します。  
  
## <a name="transformations-in-nested-containers"></a>入れ子になったコンテナー内の変換  
 次の例では、作成、<xref:System.Drawing.Graphics>オブジェクトおよびコンテナー内で<xref:System.Drawing.Graphics>オブジェクト。 ワールド変換、<xref:System.Drawing.Graphics>オブジェクトが x 方向に 100 の翻訳単位と y 軸方向に 80 単位。 コンテナーのワールド変換は、30 度回転します。 コードの呼び出しを行う`DrawRectangle(pen, -60, -30, 120, 60)`2 回クリックします。 最初の呼び出し<xref:System.Drawing.Graphics.DrawRectangle%2A>コンテナー内では、呼び出しの間には、呼び出し<xref:System.Drawing.Graphics.BeginContainer%2A>と<xref:System.Drawing.Graphics.EndContainer%2A>します。 2 番目の呼び出し<xref:System.Drawing.Graphics.DrawRectangle%2A>への呼び出し後は<xref:System.Drawing.Graphics.EndContainer%2A>します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 上記のコードでは、コンテナー内から描画する四角形が変換されるまずコンテナー (回転) のワールド変換をしのワールド変換して、<xref:System.Drawing.Graphics>オブジェクト (変換)。 ワールド変換によってのみ、コンテナーの外部から描画する四角形が変換される、<xref:System.Drawing.Graphics>オブジェクト (変換)。 次の図は、2 つの四角形を示します。 
  
 ![入れ子になったコンテナーを示す図。](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>入れ子になったコンテナーのクリッピング  
 次の例では、入れ子になったコンテナーのクリッピング領域を処理します。 このコードを作成、<xref:System.Drawing.Graphics>オブジェクトおよびコンテナー内で<xref:System.Drawing.Graphics>オブジェクト。 クリッピング領域、<xref:System.Drawing.Graphics>オブジェクトは、四角形であり、コンテナーのクリッピング領域は楕円。 コードは、2 つの呼び出し、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド。 最初の呼び出し<xref:System.Drawing.Graphics.DrawLine%2A>、コンテナーと、2 番目の呼び出しの内部<xref:System.Drawing.Graphics.DrawLine%2A>がコンテナーの範囲外です (呼び出しの後<xref:System.Drawing.Graphics.EndContainer%2A>)。 最初の行が 2 つのクリッピング領域の交差部分によって切り取られます。 クリッピング四角形領域によってのみ、2 行目のクリップ、<xref:System.Drawing.Graphics>オブジェクト。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 次の図は、2 つのクリップされた行を示しています。
  
 ![クリップされた行を含む入れ子になったコンテナーを示す図。](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 2 つの例に示すとおり、変換、およびクリッピング領域は入れ子になったコンテナーで累積されます。 コンテナーのワールド変換を設定した場合、<xref:System.Drawing.Graphics>オブジェクト、両方の変換は、コンテナー内から描画された項目に適用されます。 コンテナーの変換が適用されている最初との変換になります、<xref:System.Drawing.Graphics>オブジェクトが適用されます。 コンテナーのクリッピング領域を設定した場合、<xref:System.Drawing.Graphics>オブジェクト、コンテナーの内部から描画された項目は、重なる部分の 2 つのクリッピング領域のクリップされます。  
  
## <a name="quality-settings-in-nested-containers"></a>入れ子になったコンテナーの画質の設定  
 品質の設定 (<xref:System.Drawing.Graphics.SmoothingMode%2A>、<xref:System.Drawing.Graphics.TextRenderingHint%2A>など) で入れ子になったコンテナーは累積的な以外ではなく、コンテナーの品質設定を一時的に交換の品質設定を<xref:System.Drawing.Graphics>オブジェクト。 新しいコンテナーを作成するときに、そのコンテナーの品質設定は、既定値に設定されます。 たとえば、ある、<xref:System.Drawing.Graphics>のスムージング モードを使ってオブジェクト<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>します。 コンテナーを作成するときに、コンテナー内のスムージング モードが既定のモードをスムージングに。 自由に、コンテナーのスムージング モードを設定して、モードを設定するに従って、コンテナー内から抽出されたすべての項目が描画されます。 アイテムへの呼び出しの後に描画<xref:System.Drawing.Graphics.EndContainer%2A>スムージング モードに従ってが描画されます (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) への呼び出しの前にあった<xref:System.Drawing.Graphics.BeginContainer%2A>します。  
  
## <a name="several-layers-of-nested-containers"></a>入れ子になったコンテナーの複数のレイヤー  
 内の 1 つのコンテナーに限定されない、<xref:System.Drawing.Graphics>オブジェクト。 コンテナーのシーケンスを作成することができます、前の入れ子になった各、ワールド変換、クリッピング領域、およびこれらの入れ子になったコンテナーのそれぞれの品質設定を指定することができます。 最も内側のコンテナーから描画メソッドを呼び出す場合は、最も外側のコンテナーで最も内側のコンテナーで開始および終了の順序で、変換が適用されます。 最も内側のコンテナーから描画された項目は、重なる部分のすべてのクリッピング領域のクリップされます。  
  
 次の例では、作成、<xref:System.Drawing.Graphics>オブジェクトし、そのテキストのレンダリング ヒント設定<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>します。 コード内で他の入れ子になった 1 つ、2 つのコンテナーを作成します。 設定されている外側のコンテナーのテキストのレンダリング ヒント<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>、内側のコンテナーのテキストのレンダリング ヒントに設定されていると<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>します。 コードが 3 つの文字列を描画します。 外側のコンテナーから、からの内部コンテナーから 1 つ、<xref:System.Drawing.Graphics>オブジェクト自体。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 次の図は、3 つの文字列を示します。 描画および内部のコンテナーから、文字列、<xref:System.Drawing.Graphics>によってオブジェクトが滑らかにします。 外側のコンテナーから抽出された文字列が滑らかになってアンチ エイリアスによって、<xref:System.Drawing.Graphics.TextRenderingHint%2A>プロパティに設定されて<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>します。  
  
 ![入れ子になったコンテナーから抽出された文字列を示す図。](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics>
- [Graphics オブジェクトの状態の管理](managing-the-state-of-a-graphics-object.md)

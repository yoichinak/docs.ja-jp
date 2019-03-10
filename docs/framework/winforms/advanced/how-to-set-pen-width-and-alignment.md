---
title: '方法: セットのペンの幅と配置'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: e82f406b4fdca93df7a811eea5506846d56fda28
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703050"
---
# <a name="how-to-set-pen-width-and-alignment"></a>方法: セットのペンの幅と配置
作成するときに、 <xref:System.Drawing.Pen>、コンス トラクターに引数の 1 つとして、ペンの幅を指定することができます。 ペンの幅を変更することも、<xref:System.Drawing.Pen.Width%2A>のプロパティ、<xref:System.Drawing.Pen>クラス。  
  
 理論上の線は、幅は 0 です。 1 ピクセルの幅の線を描画するときに、理論上の線のピクセルが中央揃えされます。 1 つ以上のピクセル幅の線を描画する場合、ピクセルは理論上の線の中央揃えするかまたは、理論上の線の一方の側に表示されます。 ペンの配置プロパティを設定することができます、<xref:System.Drawing.Pen>理論上の線を基準とのペンで描画されるピクセルの配置方法を決定します。  
  
 値<xref:System.Drawing.Drawing2D.PenAlignment.Center>、 <xref:System.Drawing.Drawing2D.PenAlignment.Outset>、および<xref:System.Drawing.Drawing2D.PenAlignment.Inset>、次に表示されるコードの例のメンバーである、<xref:System.Drawing.Drawing2D.PenAlignment>列挙体。  
  
 次のコード例が 2 回線を描画します。 幅 1 の黒色のペンで 1 回と 1 回の幅が 10 の緑色のペンを使用します。  
  
### <a name="to-vary-the-width-of-a-pen"></a>ペンの幅を変更するには  
  
-   値を設定、<xref:System.Drawing.Pen.Alignment%2A>プロパティを<xref:System.Drawing.Drawing2D.PenAlignment.Center>(既定) に緑のペンで描画されるピクセルが理論上の線の中央揃えにするかを指定します。 次の図は、その結果、行を示します。  
  
     ![ペン](./media/pens1a.gif "pens1A")  
  
     次のコード例が 2 回四角形を描画します。 黒のペンの幅が 1 で 1 回と緑のペンの幅が 10 で 1 回です。  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>ペンのアラインメントを変更するには  
  
-   値を設定、<xref:System.Drawing.Pen.Alignment%2A>プロパティを<xref:System.Drawing.Drawing2D.PenAlignment.Center>四角形の境界に緑のペンで描画されるピクセルに表示することを指定します。  
  
     次の図は、結果として得られる四角形を示します。  
  
     ![ペン](./media/pens2.gif "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>ペンを作成するには  
  
-   上記のコード例では、3 番目のステートメントを次のように変更することで、緑色のペンの配置を変更します。  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     今すぐ次の図に示すようには、四角形の内側にワイド緑の線のピクセルが表示されます。  
  
     ![ペン](./media/pens3.gif "pens3")  
  
## <a name="see-also"></a>関連項目
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)

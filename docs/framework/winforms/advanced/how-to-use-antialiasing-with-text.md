---
title: '方法: テキストのアンチエイリアシングを使用します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: b0dc3cf5cff9cf3e163478861ec55a05427ad6ce
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718572"
---
# <a name="how-to-use-antialiasing-with-text"></a>方法: テキストのアンチエイリアシングを使用します。
*アンチエイリアシング*ぎざぎざのグラフィックスを描画し、外観と読みやすさを向上させるためにテキストのスムージングを参照します。 マネージで[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]クラス、低品質のテキストだけでなく高品質なアンチ エイリアス化テキストを描画できます。 通常、高品質なレンダリングでは、低品質のレンダリングよりも処理時間がかかります。 テキスト品質レベルを設定するには、設定、<xref:System.Drawing.Graphics.TextRenderingHint%2A>のプロパティを<xref:System.Drawing.Graphics>の要素の 1 つに、<xref:System.Drawing.Text.TextRenderingHint>列挙型  
  
## <a name="example"></a>例  
 次のコード例では、2 つの別々 の品質設定でテキストを描画します。  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 次の図は、コード例の出力を示しています。  
  
 ![フォント テキスト](./media/fontstext10.png "FontsText10")  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコード例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目
- [フォントとテキストの使用](using-fonts-and-text.md)

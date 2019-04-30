---
title: '方法: フォント メトリックを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 24cada3962339cae0608bbe01e070a0b8e256e73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948225"
---
# <a name="how-to-obtain-font-metrics"></a>方法: フォント メトリックを取得する
<xref:System.Drawing.FontFamily>クラスは、特定のファミリとスタイルの組み合わせに対してさまざまなメトリックを取得する次のメソッドを提供します。  
  
- <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 これらのメソッドによって返される数値は、サイズと、特定の単位から独立しているためフォント デザイン単位では<xref:System.Drawing.Font>オブジェクト。  
  
 次の図は、さまざまなメトリックを示します。  
  
 ![フォント テキスト](./media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>例  
 次の例では、Arial フォント ファミリの標準のスタイルのメトリックが表示されます。 コードを作成も、 <xref:System.Drawing.Font> 16 ピクセルのサイズと、その特定のピクセル単位のメトリックが表示されます (Arial ファミリに基づく) オブジェクト<xref:System.Drawing.Font>オブジェクト。  
  
 次の図は、コード例の出力を示します。  
  
 ![フォント テキスト](./media/csfontstext8.png "csFontsText8")  
  
 前の図の出力の最初の 2 つの行に注意してください。 <xref:System.Drawing.Font>オブジェクトは、16 のサイズを返します、<xref:System.Drawing.FontFamily>オブジェクトは、2,048 の em の高さを返します。 これら 2 つの数値 (16 と 2,048) は、キーをフォント デザイン単位と単位 (このケースのピクセル単位) の間の変換、<xref:System.Drawing.Font>オブジェクト。  
  
 たとえば、次のようにアセントをデザイン単位からピクセルに変換できます。  
  
 ![フォント テキスト](./media/fontstext9.png "FontsText9")  
  
 次のコードを配置テキスト垂直方向に設定して、<xref:System.Drawing.PointF.Y%2A>のデータ メンバーを<xref:System.Drawing.PointF>オブジェクト。 Y 座標が増加して`font.Height`テキストの新しい行はごとです。 <xref:System.Drawing.Font.Height%2A>のプロパティを<xref:System.Drawing.Font>オブジェクトがその特定の行間 (ピクセル単位) でを返す<xref:System.Drawing.Font>オブジェクト。 この例では、によって返される数<xref:System.Drawing.Font.Height%2A>19。 これは行間隔をピクセルに変換することで得られる数値 (整数に切り上げたもの) と同じであることに注意してください。  
  
 Em 高 (サイズまたは em サイズとも呼ばれます) がアセントと降下の合計ではないことに注意してください。 アセントと降下の合計には、セルの高さが呼び出されます。 内部のレディング マイナス セルの高さは、em 高さと同じです。 セルの高さと外部レディングは、線の間隔と同じです。  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [フォントとテキストの使用](using-fonts-and-text.md)

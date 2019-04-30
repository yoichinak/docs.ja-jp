---
title: '方法: 描画されたテキストにタブ ストップを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 68dbebfc4fab773fe749f9443d0c61883099d2ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967064"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>方法: 描画されたテキストにタブ ストップを設定する
テキストのタブ ストップを設定するには呼び出すことによって、<xref:System.Drawing.StringFormat.SetTabStops%2A>のメソッド、<xref:System.Drawing.StringFormat>オブジェクトを渡す、<xref:System.Drawing.StringFormat>オブジェクトを<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラス。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>を使用して既存のタブを展開することができますが、描画するテキストへのタブ位置の追加サポートされていませんが停止しますが、<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>フラグ。  
  
## <a name="example"></a>例  
 次の例では、150、250、350 にタブ ストップを設定します。 次に、コードでは、名前とテストの点数のタブ付きの一覧が表示されます。  
  
 次の図は、タブ付きのテキストを示します。  
  
 ![タブ付きの名前とスコアの一覧を示すスクリーン ショット。](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 次のコードが 2 つの引数を渡す、<xref:System.Drawing.StringFormat.SetTabStops%2A>メソッド。 2 番目の引数は、タブのオフセットを含む配列です。 渡される最初の引数<xref:System.Drawing.StringFormat.SetTabStops%2A>は 0、0、外接する四角形の左端の位置から配列内の最初のオフセットを測定することです。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- [フォントとテキストの使用](using-fonts-and-text.md)
- [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)

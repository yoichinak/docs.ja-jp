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
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947819"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>方法: 描画されたテキストにタブ ストップを設定する
<xref:System.Drawing.StringFormat.SetTabStops%2A> オブジェクトのメソッドを<xref:System.Drawing.StringFormat>呼び出して<xref:System.Drawing.Graphics.DrawString%2A> 、<xref:System.Drawing.Graphics>そのオブジェクトをクラスのメソッドに渡すことで、テキストのタブストップを設定できます。 <xref:System.Drawing.StringFormat>  
  
> [!NOTE]
> は<xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> 、描画されたテキストへのタブストップの追加をサポートしていません<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>が、フラグを使用して既存のタブストップを展開することはできます。  
  
## <a name="example"></a>例  
 次の例では、150、250、および350でタブストップを設定します。 次に、コードは、名前とテストスコアのタブ付きリストを表示します。  
  
 次の図は、タブ付きテキストを示しています。  
  
 ![タブ付きの名前とスコアの一覧を示すスクリーンショット。](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 次のコードでは、 <xref:System.Drawing.StringFormat.SetTabStops%2A>メソッドに2つの引数を渡します。 2番目の引数は、タブオフセットを格納する配列です。 に<xref:System.Drawing.StringFormat.SetTabStops%2A>渡される最初の引数は0です。これは、配列内の最初のオフセットが、外接する四角形の左端である位置0から測定されることを示します。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- 前の例は、Windows フォームで使用するように設計さ<xref:System.Windows.Forms.PaintEventArgs>れています。これ<xref:System.Windows.Forms.PaintEventHandler>は、のパラメーターであるを必要`e`とします。  
  
## <a name="see-also"></a>関連項目

- [フォントとテキストの使用](using-fonts-and-text.md)
- [方法: GDI を使用してテキストを描画する](how-to-draw-text-with-gdi.md)

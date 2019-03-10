---
title: '方法: 描画されたテキストにタブ ストップを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 2b3d019db1fd3e9eeb9def1c18b54d293e5faca9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722426"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>方法: 描画されたテキストにタブ ストップを設定します。
テキストのタブ ストップを設定するには呼び出すことによって、<xref:System.Drawing.StringFormat.SetTabStops%2A>のメソッド、<xref:System.Drawing.StringFormat>オブジェクトを渡す、<xref:System.Drawing.StringFormat>オブジェクトを<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラス。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>を使用して既存のタブを展開することができますが、描画するテキストへのタブ位置の追加サポートされていませんが停止しますが、<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>フラグ。  
  
## <a name="example"></a>例  
 次の例では、150、250、350 にタブ ストップを設定します。 次に、コードでは、名前とテストの点数のタブ付きの一覧が表示されます。  
  
 次の図は、タブ付きのテキストを示します。  
  
 ![フォント テキスト](./media/fontstext4.png "fontstext4")  
  
 次のコードが 2 つの引数を渡す、<xref:System.Drawing.StringFormat.SetTabStops%2A>メソッド。 2 番目の引数は、タブのオフセットを含む配列です。 渡される最初の引数<xref:System.Drawing.StringFormat.SetTabStops%2A>は 0、0、外接する四角形の左端の位置から配列内の最初のオフセットを測定することです。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目
- [フォントとテキストの使用](using-fonts-and-text.md)
- [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)

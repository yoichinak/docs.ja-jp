---
title: フォントとテキストの使用
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769419"
---
# <a name="using-fonts-and-text"></a>フォントとテキストの使用
によって提供されるいくつかのクラスがある[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]Windows フォームにテキストを描画するためです。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics>クラスにはいくつか<xref:System.Drawing.Graphics.DrawString%2A>外接する四角形、フォント、および形式の場所などのテキストのさまざまな機能を指定するためのメソッド。 さらに、描画、テキストを計測[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]静的<xref:System.Windows.Forms.TextRenderer.DrawText%2A>と<xref:System.Windows.Forms.TextRenderer.MeasureText%2A>によって提供されるメソッド、`TextRenderer`クラス。 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]メソッドの場所、フォント、および形式を指定することも可能です。 いずれも使用できます[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]または[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]テキスト レンダリングされます。 ただし、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]通常をより的確にパフォーマンスとより正確なテキストを測定します。 テキストのレンダリングに影響を与える他のクラスには`FontFamily`、 `Font`、 <xref:System.Drawing.StringFormat>、および`TextFormatFlags`します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: フォント ファミリとフォントを作成します。](how-to-construct-font-families-and-fonts.md)  
 作成する方法を示します`Font`と`FontFamily`オブジェクト。  
  
 [方法: 指定した位置のテキストの描画](how-to-draw-text-at-a-specified-location.md)  
 特定の場所を使用して、テキストを描画する方法について説明します[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]します。  
  
 [方法: 四角形内にテキストを折り返して描画](how-to-draw-wrapped-text-in-a-rectangle.md)  
 使用して、四角形内のテキストを描画する方法について説明します[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]します。  
  
 [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)  
 使用する方法を示します[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]テキストの描画します。  
  
 [方法: 描画するテキストを揃える](how-to-align-drawn-text.md)  
 書式設定する方法を示しています。[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]テキスト。  
  
 [方法: 垂直方向のテキストを作成します。](how-to-create-vertical-text.md)  
 垂直方向に配置されたテキストを描画する方法について説明します[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]します。  
  
 [方法: 描画されたテキストにタブ ストップを設定します。](how-to-set-tab-stops-in-drawn-text.md)  
 表示方法でタブ位置でテキストの描画[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]します。  
  
 [方法: インストールされているフォントを列挙します。](how-to-enumerate-installed-fonts.md)  
 インストールされているフォントの名前を一覧表示する方法について説明します。  
  
 [方法: プライベート フォント コレクションを作成します。](how-to-create-a-private-font-collection.md)  
 作成する方法について説明します、<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。  
  
 [方法: フォント メトリックを取得します。](how-to-obtain-font-metrics.md)  
 セル アセント降下などのフォント メトリックを取得する方法を示します。  
  
 [方法: テキストのアンチエイリアシングを使用します。](how-to-use-antialiasing-with-text.md)  
 テキストを描画するときにアンチエイリアシングを使用する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Drawing.Font>  
 このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。  
  
 <xref:System.Drawing.FontFamily>  
 このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。  
  
 <xref:System.Windows.Forms.TextRenderer>  
 このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。

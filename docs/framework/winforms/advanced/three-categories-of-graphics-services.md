---
title: グラフィックス サービスの 3 つのカテゴリ
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: a69fa7a1ccad353c879731de05dc47f0d6ae8795
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505233"
---
# <a name="three-categories-of-graphics-services"></a>グラフィックス サービスの 3 つのカテゴリ
Windows フォームでグラフィックスの提供は、次の 3 つの広範なカテゴリに分類されます。  
  
- 2 次元 (2-d) のベクター グラフィックス  
  
- イメージング  
  
- タイポグラフィ  
  
## <a name="2-d-vector-graphics"></a>2 次元ベクター グラフィックス  
 2 次元ベクター グラフィックスはプリミティブです。直線、曲線、および図表; など座標系のポイントのセットによって指定されています。 たとえば、直線がその 2 つのエンドポイントで指定され、四角形の左上隅にあると、幅と高さを定義する数値の 1 組の位置を示す点で指定します。 単純なパスは、直線で接続されている点の配列によって指定されます。 ベジエ スプラインは、4 つのコントロール ポイントで指定された高度な曲線です。  
  
 GDI + 自体、プリミティブを描画する方法についての情報を格納するクラスおよびクラスを実際に描画を実行するクラスと、プリミティブについての情報を格納する構造体を提供します。 など、<xref:System.Drawing.Rectangle>構造体に格納する四角形のサイズと場所、<xref:System.Drawing.Pen>クラスは、線の色、線の幅、および線のスタイルに関する情報を格納し、<xref:System.Drawing.Graphics>クラスには、線、四角形、パスを描画するためのメソッドとその他の数値。 あるいくつかも<xref:System.Drawing.Brush>方法に関する情報を格納するクラスの終了図形とパスが色やパターンで塗りつぶされます。  
  
 メタファイルには、一連のグラフィック コマンドには、ベクター イメージを記録できます。 GDI + は、提供、<xref:System.Drawing.Imaging.Metafile>記録、表示、およびメタファイルを保存するためのクラス。 <xref:System.Drawing.Imaging.MetafileHeader>と<xref:System.Drawing.Imaging.MetaHeader>クラス、メタファイル ヘッダーに格納されたデータを検査することができます。  
  
## <a name="imaging"></a>イメージング  
 特定の種類の画像は、困難または不可能なベクター グラフィックスの手法で表示されます。 たとえば、ツール バー ボタンの画像やアイコンとして表示される画像は、直線と曲線のコレクションとして指定する困難です。 混雑した野球場の高解像度デジタル写真はベクター手法を作成するさらに難しくなります。 このタイプのイメージはビットマップで、画面上の個々 のドットの色を表す数値の配列として格納されます。 GDI + は、提供、<xref:System.Drawing.Bitmap>を表示する、操作、およびビットマップの保存のクラス。  
  
## <a name="typography"></a>タイポグラフィ  
 文字体裁は、さまざまなフォント、サイズ、およびスタイル内のテキストの表示です。 GDI + この複雑なタスクの広範なサポートを提供します。 GDI + での新しい機能の 1 つは、サブピクセル アンチ エイリアスによりテキストをより滑らかな外観は、LCD 画面に描画します。  
  
 Windows フォームが GDI 機能を持つテキストを描画するオプションを提供するさらに、その<xref:System.Windows.Forms.TextRenderer>クラス。  
  
## <a name="see-also"></a>関連項目

- [グラフィックスの概要](graphics-overview-windows-forms.md)
- [GDI+ マネージド コードについて](about-gdi-managed-code.md)
- [マネージド グラフィックス クラスの使用](using-managed-graphics-classes.md)

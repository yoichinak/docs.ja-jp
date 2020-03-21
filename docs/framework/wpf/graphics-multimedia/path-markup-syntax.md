---
title: パス マークアップ構文
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: adcedcea6c8d6d988021cbbccf87bd25a042fd16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181861"
---
# <a name="path-markup-syntax"></a>パス マークアップ構文
パスについては[、「WPF の図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)」と[「ジオメトリの概要](geometry-overview.md)」で説明されていますが、このトピックでは、パス ジオメトリをよりコンパクトに指定するために使用できる強力で複雑なミニ言語について[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]詳しく説明します。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、オブジェクトの<xref:System.Windows.Media.Geometry>基本的な機能を理解している必要があります。 詳細については、「[ジオメトリの概要](geometry-overview.md)」を参照してください。  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry ミニ言語と PathFigureCollection ミニ言語  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、ジオメトリック パスを記述するためのミニ言語を提供する<xref:System.Windows.Media.StreamGeometry> <xref:System.Windows.Media.PathFigureCollection>2 つのクラスがあります。  
  
- ミニ言語は<xref:System.Windows.Media.StreamGeometry>、 のプロパティや要素のプロパティなど<xref:System.Windows.Media.Geometry>、 type<xref:System.Windows.UIElement.Clip%2A>の<xref:System.Windows.UIElement>プロパティを<xref:System.Windows.Shapes.Path.Data%2A>設定するときに使用します。 <xref:System.Windows.Shapes.Path> 次の例では、属性構文を使用<xref:System.Windows.Media.StreamGeometry>して を作成します。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- のプロパティを<xref:System.Windows.Media.PathFigureCollection>設定するときにミニ言語を<xref:System.Windows.Media.PathGeometry.Figures%2A>使用します。 <xref:System.Windows.Media.PathGeometry> 次の例では、属性構文を使用して<xref:System.Windows.Media.PathFigureCollection>の<xref:System.Windows.Media.PathGeometry>を作成します。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 前の例からわかるように、2 つのミニ言語はほとんど同じです。 を使用できるどんな状況<xref:System.Windows.Media.PathGeometry>でも、常に使用することができます。 <xref:System.Windows.Media.StreamGeometry>だから、あなたはどちらを使用する必要がありますか? パスを<xref:System.Windows.Media.StreamGeometry>作成した後で変更する必要がない場合は、 を使用します。パスを<xref:System.Windows.Media.PathGeometry>変更する必要がある場合は a を使用します。  
  
 オブジェクト<xref:System.Windows.Media.PathGeometry>と<xref:System.Windows.Media.StreamGeometry>オブジェクトの違いの詳細については、「[ジオメトリの概要](geometry-overview.md)」を参照してください。  
  
### <a name="a-note-about-white-space"></a>空白についてのメモ  
 簡潔にするために、この後のセクションで示す構文には 1 つの空白が使用されていますが、1 つの空白を使用できるところでは、常に複数の空白スペースも許容されます。  
  
 2 つの数値は、実際にはコンマまたは空白で区切る必要はありませんが、結果の文字列が明確でない場合にのみ行うことができます。 たとえば、`2..3`実際には2つの数字です。 と ".3" ) です。 同様に`2-3`、"2" と "-3" です。 どちらの場合も、コマンドの前後に空白は必要ありません。  
  
### <a name="syntax"></a>構文  
 属性[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の使用法の構文<xref:System.Windows.Media.StreamGeometry>は、オプション<xref:System.Windows.Media.FillRule>の値と 1 つ以上の図形の説明で構成されます。  
  
|StreamGeometry XAML 属性使用構文|  
|-----------------------------------------|  
|`<`*オブジェクト**property*`="`プロパティ`fillRule` `figureDescription`[ `figureDescription`] [ ]`" ... />`|  
  
 属性[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の使用法は<xref:System.Windows.Media.PathFigureCollection>、1 つ以上の図形の説明で構成されます。  
  
|PathFigureCollection XAML 属性使用構文|  
|-----------------------------------------------|  
|`<`*オブジェクト**property*`="``figureDescription`プロパティ`figureDescription`[ ]*`" ... />`|  
  
|期間|説明|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> が を<xref:System.Windows.Media.StreamGeometry>使用<xref:System.Windows.Media.FillRule.EvenOdd>するかどうかを指定<xref:System.Windows.Media.FillRule.Nonzero><xref:System.Windows.Media.PathGeometry.FillRule%2A>します。<br /><br /> -   `F0`塗りつぶし<xref:System.Windows.Media.FillRule.EvenOdd>ルールを指定します。<br />-   `F1`塗りつぶし<xref:System.Windows.Media.FillRule.Nonzero>ルールを指定します。<br /><br /> このコマンドを省略すると、サブパスはデフォルトの動作<xref:System.Windows.Media.FillRule.EvenOdd>(. このコマンドを指定する場合は、先頭に配置する必要があります。|  
|*figureDescription*|移動コマンドと描画コマンド (および省略可能な閉じるコマンド) で構成される図形。<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|図形の開始位置を指定する移動コマンド。 「[移動コマンド](#themovecommand)」セクションを参照してください。|  
|*drawCommands*|図の内容を記述する 1 つまたは複数の描画コマンド。 「[コマンドの描画](#drawcommands)」セクションを参照してください。|  
|*closeCommand*|図形を閉じるコマンド (省略可能)。 「[コマンドを閉じる](#closecommand)」セクションを参照してください。|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>移動コマンド  
 新しい図形の始点を指定します。  
  
|構文|  
|------------|  
|`M`*スタートポイント*<br /><br /> - または -<br /><br /> `m`*スタートポイント*|  
  
|期間|説明|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 新しい図形の始点。|  
  
 大文字`M`は絶対値であることを`startPoint`示します。小文字`m`は、前`startPoint`の点へのオフセットであることを示し、(0,0) が存在しない場合は、その点を示します。 移動コマンドの後ろに複数の点を指定した場合は、直線コマンドを指定した場合でも、これらの点を結ぶ線が描画されます。  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>描画コマンド  
 描画コマンドは、さまざまな図形コマンドで構成できます。 次の図形のコマンドを使用できます。直線、水平線、垂直線、3 次ベジエ曲線、2 次ベジエ曲線、スムーズ 3 次ベジエ曲線、スムーズ 2 次ベジエ曲線、および楕円の円弧。  
  
 各コマンドは、大文字または小文字で入力します。大文字は絶対値を、小文字は相対値を表し、そのセグメントの制御点は、前の例の終点を基準とします。 同じタイプの複数のコマンドを順次入力する場合は、重複するコマンド入力を省略できます。たとえば、`L 100,200 300,400`と同じ`L 100,200 L 300,400`値を使用します。 次の表では、**移動**コマンドと**描画**コマンドについて説明します。  
  
### <a name="line-command"></a>直線コマンド  
 現在の点と指定された終点の間に直線を作成します。 `l 20 30`有効`L 20,30`な**行**コマンドの例です。  
  
|構文|  
|------------|  
|`L`*エンドポイント*<br /><br /> - または -<br /><br /> `l`*エンドポイント*|  
  
|期間|説明|  
|----------|-----------------|  
|*エンドポイント*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 線の終点。|  

大文字`L`は絶対値であることを`endPoint`示します。小文字`l`は、前`endPoint`の点へのオフセットであることを示し、(0,0) が存在しない場合は、その点を示します。

### <a name="horizontal-line-command"></a>水平線コマンド  
 現在の点と指定された x 座標の間に水平線を作成します。 `H 90` は、有効な水平線コマンドの例です。

|構文|  
|------------|  
|`H`  *X*<br /><br /> - または -<br /><br /> `h`  *X*|  
  
|期間|説明|  
|----------|-----------------|  
|*X*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 直線の終点の x 座標。|  
  
大文字`H`は絶対値であることを`x`示します。小文字`h`は、前`x`の点へのオフセットであることを示し、(0,0) が存在しない場合は、その点を示します。
  
### <a name="vertical-line-command"></a>垂直線コマンド  
 現在の点と指定された y 座標の間に垂直線を作成します。 `v 90` は、有効な垂直線コマンドの例です。

|構文|  
|------------|  
|`V`  *Y*<br /><br /> - または -<br /><br /> `v`  *Y*|  
  
|期間|説明|  
|----------|-----------------|  
|*Y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 直線の終点の y 座標。|  

大文字`V`は絶対値であることを`y`示します。小文字`v`は、前`y`の点へのオフセットであることを示し、(0,0) が存在しない場合は、その点を示します。  

### <a name="cubic-bezier-curve-command"></a>3 次ベジエ曲線コマンド  
 指定した 2 つのコントロール ポイント (1`controlPoint`と`controlPoint`2) を使用して、現在の点と指定した終点の間に 3 次ベジエ曲線を作成します。 `C 100,200 200,400 300,200` は、有効な曲線コマンドの例です。  
  
|構文|  
|------------|  
|`C``controlPoint`1`controlPoint`2`endPoint`<br /><br /> - または -<br /><br /> `c``controlPoint`1`controlPoint`2`endPoint`|  
  
|期間|説明|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線の 1 つ目の制御点。曲線の前半の接線を決定します。|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線の 2 つ目の制御点。曲線の後半の接線を決定します。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線が描画される点。|  
  
### <a name="quadratic-bezier-curve-command"></a>2 次ベジエ曲線コマンド  
 指定されたコントロール ポイント ()`controlPoint`を使用して、現在の点と指定した終点の間に 2 次ベジエ曲線を作成します。 `q 100,200 300,200` は、有効な 2 次ベジエ曲線コマンドの例です。  
  
|構文|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - または -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|期間|説明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線の制御点。曲線の前半と後半の接線を決定します。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線が描画される点。|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>スムーズ 3 次ベジエ曲線コマンド  
 現在の点と指定された終点の間に 3 次ベジエ曲線を作成します。 1 つ目の制御点は、現在の点に対する前のコマンドの 2 つ目の制御点のリフレクションと見なされます。 前のコマンドが存在しない場合、または前のコマンドが 3 次ベジエ曲線コマンドまたはスムーズ 3 次ベジエ曲線コマンドでなかった場合、1 つ目の制御点は、現在の点と一致するとみなされます。 2 番目の制御点は、曲線の終点の制御点で、2`controlPoint`で指定されます。 たとえば、`S 100,200 200,300`有効なスムーズな 3 次ベジェ曲線コマンドです。  
  
|構文|  
|------------|  
|`S``controlPoint`2`endPoint`<br /><br /> - または -<br /><br /> `s``controlPoint`2`endPoint`|  
  
|期間|説明|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線の制御点。曲線の後半の接線を決定します。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線が描画される点。|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>スムーズ 2 次ベジエ曲線コマンド  
 現在の点と指定された終点の間に 2 次ベジエ曲線を作成します。 制御点は、現在の点に対する前のコマンドの制御点のリフレクションと見なされます。 前のコマンドが存在しない場合、または前のコマンドが 2 次ベジエ曲線コマンドまたはスムーズ 2 次ベジエ曲線コマンドでなかった場合、制御点は、現在の点と一致するとみなされます。  
  
|構文|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - または -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|期間|説明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線の制御点。曲線の前半の接線を決定します。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線が描画される点。|  
  
### <a name="elliptical-arc-command"></a>楕円の円弧コマンド  
 現在の点と指定された終点の間に楕円の円弧を作成します。  
  
|構文|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - または -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|期間|説明|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> 円弧の x 半径と y 半径。|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 楕円の回転 (度単位)。|  
|`isLargeArcFlag`|円弧の角度を 180 度以上にする場合は 1 に設定します。それ以外の場合は 0 に設定します。|  
|`sweepDirectionFlag`|円弧が正の角度の方向に描画される場合は 1 に設定します。それ以外の場合は 0 に設定します。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 円弧が描画される点。|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>閉じるコマンド  
 現在の図形を終了し、現在の点と図の開始点を結ぶ線を作成します。 このコマンドは、図形の最初のセグメントと最後のセグメントの間に線結合 (コーナー) を作成します。  
  
|構文|  
|------------|  
|`Z`<br /><br /> - または -<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>点の構文  
 (0,0) が左上隅である点の x 座標と y 座標を記述します。
  
|構文|  
|------------|  
|`x` `,` `y`<br /><br /> - または -<br /><br /> `x` `y`|  
  
|期間|説明|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 点の x 座標。|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 点の y 座標。|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>特殊な値  
 標準的な数値ではなく、次の特殊な値を使用することもできます。 これらの値では、大文字と小文字が区別されます。  
  
 Infinity  
 を<xref:System.Double.PositiveInfinity?displayProperty=nameWithType>表します。  
  
 -Infinity  
 を<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>表します。  
  
 (NaN)  
 を<xref:System.Double.NaN?displayProperty=nameWithType>表します。  
  
 指数表記を使用することもできます。 たとえば、`+1.e17` は有効な値です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [ジオメトリの概要](geometry-overview.md)
- [ハウツートピック](geometries-how-to-topics.md)

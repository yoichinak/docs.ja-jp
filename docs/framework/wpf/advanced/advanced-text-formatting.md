---
title: テキストの高度な書式設定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
ms.openlocfilehash: 0d3b44007524f502d8393d1dc1834142090a7a15
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238654"
---
# <a name="advanced-text-formatting"></a>テキストの高度な書式設定
Windows Presentation Foundation (WPF) は、テキストを含む、アプリケーションでの堅牢な Api のセットを提供します。 レイアウトと[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]Api など<xref:System.Windows.Controls.TextBlock>、最も一般的な提供および一般的な要素を使用して、テキスト表示にします。 などの Api を描画<xref:System.Windows.Media.GlyphRunDrawing>と<xref:System.Windows.Media.FormattedText>図面の書式設定されたテキストを含めるための手段を提供します。 高度なレベルでは、一番[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張可能なテキストを書式設定テキスト プレゼンテーションでは、テキスト保管管理、テキスト ラン書式設定の管理、および埋め込みオブジェクト管理などのすべての側面を制御するエンジンを提供します。  
  
 このトピックでは、概要[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]テキストの書式設定します。 クライアント実装との使用に焦点を当てます、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]テキスト書式設定エンジンです。  
  
> [!NOTE]
>  このドキュメント内のすべてのコード例が記載されて、[高度なテキストの書式設定サンプル](https://go.microsoft.com/fwlink/?LinkID=159965)します。  

<a name="prereq"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、テキスト表示に使用されるより高レベル Api に精通していることを前提としています。 ほとんどのユーザー シナリオでは、高度なテキストのこのトピックで説明されている Api を書式設定は必要ありません。 別のテキストの Api の概要については、次を参照してください。 [WPF のドキュメント](documents-in-wpf.md)します。  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 テキストのレイアウトと[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]でコントロールを[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションに簡単に書式設定されたテキストを追加するための書式設定のプロパティを提供します。 これらのコントロールでは、テキストの表示を処理するさまざまなプロパティが公開されます。書体、大きさ、色などです。 通常の状況では、これらのコントロールはアプリケーションの大半のテキスト表示を処理できます。 しかしながら、一部の高度なシナリオでは、テキスト表示と同様にテキスト保存を制御する必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、その目的のための拡張テキスト書式設定エンジンを提供します。  
  
 高度なテキストを書式設定機能がある[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]エンジン、テキスト ストア、テキスト ラン、書式設定と書式設定プロパティのテキストで構成されます。 テキストの書式設定エンジン、<xref:System.Windows.Media.TextFormatting.TextFormatter>プレゼンテーションに使用するテキスト行を作成します。 これは、行の書式設定プロセスを開始し、テキスト フォーマッタを呼び出すことによって実現されます<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>します。 テキスト フォーマッタは、テキスト ストアからテキスト ランを取得しますを呼び出し、ストアの<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>メソッド。 <xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトを形成し<xref:System.Windows.Media.TextFormatting.TextLine>テキスト フォーマッタによりオブジェクト検査または表示するため、アプリケーションが与えられます。  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>テキスト フォーマッタを使用する  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]テキストの書式設定エンジンし、書式設定して、テキスト行の改行のサービスを提供します。 テキスト フォーマッタは、さまざまなテキスト文字書式や段落スタイルを処理し、国際的なテキスト レイアウトに対応しています。  
  
 従来のテキスト、API とは異なり、<xref:System.Windows.Media.TextFormatting.TextFormatter>一連のコールバック メソッドを介してテキスト レイアウト クライアントと対話します。 クライアントは、これらのメソッドの実装を提供する必要があります、<xref:System.Windows.Media.TextFormatting.TextSource>クラス。 次の図は、クライアント アプリケーション間でテキスト レイアウトの相互作用と<xref:System.Windows.Media.TextFormatting.TextFormatter>します。  
  
 ![テキスト レイアウト クライアントと TextFormatter のダイアグラム](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 テキスト フォーマッタを使用して、テキスト ストアから書式設定されたテキスト行を取得するの実装である<xref:System.Windows.Media.TextFormatting.TextSource>します。 これを使用して、テキスト フォーマッタのインスタンスを作成することで、<xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>メソッド。 このメソッドはテキスト フォーマッタのインスタンスを作成し、行の高さと幅の最大値を設定します。 行の作成プロセスを呼び出すことによって開始テキスト フォーマッタのインスタンスを作成するとすぐ、<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>メソッド。 <xref:System.Windows.Media.TextFormatting.TextFormatter> 呼び出して、テキストとテキスト ランの書式設定パラメーターを取得するテキスト ソースを構成する行。  
  
 次の例は、テキスト ストアを書式設定するプロセスを示しています。 <xref:System.Windows.Media.TextFormatting.TextFormatter>オブジェクトは、テキスト ストアからテキスト行を取得し、テキスト行に描画をフォーマットするために使用、<xref:System.Windows.Media.DrawingContext>します。  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>クライアント テキスト ストアを実装する  
 テキスト書式設定エンジンを拡張するとき、テキスト ストアのあらゆる側面を実装し、管理する必要があります。 これは簡単な作業ではありません。 テキスト ストアは、テキスト ランのプロパティ、段落のプロパティ、埋め込みオブジェクト、その他の同様のコンテンツの追跡を担当します。 個人とテキスト フォーマッタも用意されています<xref:System.Windows.Media.TextFormatting.TextRun>テキスト フォーマッタを使用して作成するオブジェクト<xref:System.Windows.Media.TextFormatting.TextLine>オブジェクト。  
  
 テキスト ストアの仮想化を処理するために、テキスト ストアをから派生する必要があります<xref:System.Windows.Media.TextFormatting.TextSource>します。 <xref:System.Windows.Media.TextFormatting.TextSource> テキスト フォーマッタを使用して、テキスト ストアからテキスト ランを取得するメソッドを定義します。 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> 行の書式設定で使用されるテキストを取得するテキスト フォーマッタで使用されるメソッドを実行します。 呼び出し<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>次の条件のいずれかが発生するまでに、テキスト フォーマッタによって繰り返し行われました。  
  
- A<xref:System.Windows.Media.TextFormatting.TextEndOfLine>またはサブクラスが返されます。  
  
- テキスト ランの幅が累積されはテキスト フォーマッタを作成するか、通話またはテキスト フォーマッタへの呼び出しで指定された行の最大の幅を超える<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>メソッド。  
  
- A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] "CF"、"LF"、"CRLF"などの改行シーケンスが返されます。  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>テキスト ランを提供する  
 テキスト書式設定プロセスの中心となるものは、テキスト フォーマッタとテキスト ストアの間のやりとりです。 実装<xref:System.Windows.Media.TextFormatting.TextSource>はテキスト フォーマッタの提供、<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトとテキストを実行すると、書式設定プロパティ。 この相互作用がによって処理される、<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>メソッドで、テキスト フォーマッタによって呼び出されます。  
  
 次の表は、定義済みのいくつか<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクト。  
  
|TextRun の種類|使用法|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|文字グリフの表示をテキスト フォーマッタに返すために使用される特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|テキスト内のボタンやイメージなど、測定、ヒット テスト、描画が全部行われるコンテンツを提供するための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|行の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|段落の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|直前の影響を受ける範囲の終わりなど、セグメントの末尾をマークするために使用された特殊なテキスト ラン<xref:System.Windows.Media.TextFormatting.TextModifier>を実行します。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|隠れ文字の範囲をマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|その範囲でテキスト ランのプロパティを変更するための特殊なテキスト ラン。 次の一致するまで、スコープ<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>テキスト ランまで、または次<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>します。|  
  
 定義済みの<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトをサブクラス化できます。 それにより、テキスト ソースはテキスト フォーマッタにカスタム データを含むテキスト ランを提供できます。  
  
 次の例で、<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>メソッド。 このテキスト ストア<xref:System.Windows.Media.TextFormatting.TextRun>テキスト フォーマッタに処理するオブジェクト。  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  この例では、テキスト ストアはすべてのテキストに同じテキスト プロパティを提供します。 高度なテキスト ストアでは、場合によっては、独自のスパン管理を実装し、個々の文字に異なるプロパティを与えるようにする必要があります。  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>書式設定プロパティを指定する  
 <xref:System.Windows.Media.TextFormatting.TextRun> オブジェクトは、テキスト ストアが提供するプロパティを使用して書式設定します。 これらのプロパティは、2 つの種類、<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>と<xref:System.Windows.Media.TextFormatting.TextRunProperties>します。 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> 段落の包括的なプロパティを処理します。<xref:System.Windows.TextAlignment>と<xref:System.Windows.FlowDirection>します。 <xref:System.Windows.Media.TextFormatting.TextRunProperties> 各テキスト ラン、前景ブラシなど、段落内のさまざまなことができるプロパティは<xref:System.Windows.Media.Typeface>、およびフォント サイズ。 カスタム段落やカスタム テキスト ラン プロパティ タイプを実装するアプリケーションがから派生するクラスを作成する必要があります<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>と<xref:System.Windows.Media.TextFormatting.TextRunProperties>それぞれします。  
  
## <a name="see-also"></a>関連項目

- [WPF のタイポグラフィ](typography-in-wpf.md)
- [WPF のドキュメント](documents-in-wpf.md)

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
ms.openlocfilehash: 745d20e0bd4f877f9d4559f9fc7829b56689d35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185942"
---
# <a name="advanced-text-formatting"></a>テキストの高度な書式設定
Windows プレゼンテーションファンデーション (WPF) は、アプリケーションにテキストを含める堅牢な API セットを提供します。 レイアウトや[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]API などは<xref:System.Windows.Controls.TextBlock>、テキストプレゼンテーションの最も一般的で一般的な要素を提供します。 や などの<xref:System.Windows.Media.GlyphRunDrawing><xref:System.Windows.Media.FormattedText>描画 API は、フォーマットされたテキストを図面に含める手段を提供します。 WPFWPF は、テキスト ストア管理、テキスト ランの書式設定管理、埋め込みオブジェクト管理など、テキスト表示のあらゆる側面を制御する拡張可能なテキスト書式設定エンジンを提供します。  
  
 このトピックでは、WPF テキストの書式設定の概要について説明します。 クライアントの実装と WPF テキスト書式設定エンジンの使用に焦点を当てています。  
  
> [!NOTE]
> このドキュメント内のすべてのコード例については、「[高度なテキストフォーマットのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting)」を参照してください。  

<a name="prereq"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、テキストプレゼンテーションに使用される上位レベルの API について理解していることを前提としています。 ほとんどのユーザー シナリオでは、このトピックで説明する高度なテキスト形式 API は必要ありません。 さまざまなテキスト API の概要については、「 [WPF のドキュメント](documents-in-wpf.md)」を参照してください。  
  
<a name="section1"></a>
## <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 WPF のテキスト[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]レイアウトとコントロールは、書式設定されたテキストをアプリケーションに簡単に含めることができるように書式設定プロパティを提供します。 これらのコントロールでは、テキストの表示を処理するさまざまなプロパティが公開されます。書体、大きさ、色などです。 通常の状況では、これらのコントロールはアプリケーションの大半のテキスト表示を処理できます。 しかしながら、一部の高度なシナリオでは、テキスト表示と同様にテキスト保存を制御する必要があります。 WPF には、この目的に対応した拡張可能なテキスト書式設定エンジンが用意されています。  
  
 WPF WPF で使用されている高度なテキスト書式設定機能は、テキスト書式設定エンジン、テキスト ストア、テキスト ラン、および書式設定プロパティで構成されています。 テキスト書式設定エンジン は<xref:System.Windows.Media.TextFormatting.TextFormatter>、プレゼンテーションに使用するテキスト行を作成します。 これは、行の書式設定プロセスを実行し、テキスト フォーマッタの を呼び出<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>すことによって実現されます。 テキスト フォーマッタは、ストアの<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>メソッドを呼び出すことによって、テキスト ストアからテキスト ランを取得します。 オブジェクト<xref:System.Windows.Media.TextFormatting.TextRun>はテキストフォーマッタ<xref:System.Windows.Media.TextFormatting.TextLine>によってオブジェクトに形成され、アプリケーションに検査または表示用に与えられます。  
  
<a name="section2"></a>
## <a name="using-the-text-formatter"></a>テキスト フォーマッタを使用する  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>は WPF テキスト書式設定エンジンであり、テキスト行の書式設定と改行を行うためのサービスを提供します。 テキスト フォーマッタは、さまざまなテキスト文字書式や段落スタイルを処理し、国際的なテキスト レイアウトに対応しています。  
  
 従来のテキスト API と<xref:System.Windows.Media.TextFormatting.TextFormatter>は異なり、コールバック メソッドのセットを通じてテキスト レイアウト クライアントと対話します。 クライアントは、クラスの実装でこれらのメソッドを提供する必要<xref:System.Windows.Media.TextFormatting.TextSource>があります。 次の図は、クライアント アプリケーションと のテキスト レイアウト<xref:System.Windows.Media.TextFormatting.TextFormatter>の相互作用を示しています。  
  
 ![テキスト レイアウト クライアントと TextFormatter のダイアグラム](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 テキスト フォーマッタは、テキスト ストアから書式設定されたテキスト行を取得するために使用されます<xref:System.Windows.Media.TextFormatting.TextSource>。 これは、まずメソッドを使用してテキスト フォーマッタのインスタンスを<xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>作成することによって行われます。 このメソッドはテキスト フォーマッタのインスタンスを作成し、行の高さと幅の最大値を設定します。 テキスト フォーマッタのインスタンスが作成されると、すぐにメソッドを呼び出して行作成プロセスが<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>開始されます。 <xref:System.Windows.Media.TextFormatting.TextFormatter>行を形成するテキストの実行のテキストと書式設定パラメーターを取得するために、テキスト ソースに戻ります。  
  
 次の例は、テキスト ストアを書式設定するプロセスを示しています。 オブジェクト<xref:System.Windows.Media.TextFormatting.TextFormatter>は、テキスト ストアからテキスト行を取得し、テキスト行を に描画する書式を<xref:System.Windows.Media.DrawingContext>設定するために使用されます。  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>
## <a name="implementing-the-client-text-store"></a>クライアント テキスト ストアを実装する  
 テキスト書式設定エンジンを拡張するとき、テキスト ストアのあらゆる側面を実装し、管理する必要があります。 これは簡単な作業ではありません。 テキスト ストアは、テキスト ランのプロパティ、段落のプロパティ、埋め込みオブジェクト、その他の同様のコンテンツの追跡を担当します。 また、テキスト フォーマッタがオブジェクト<xref:System.Windows.Media.TextFormatting.TextRun>を作成するために使用する個々のオブジェクトを<xref:System.Windows.Media.TextFormatting.TextLine>使用して、テキスト フォーマッタを提供します。  
  
 テキスト ストアの仮想化を処理するには、テキスト ストアを から<xref:System.Windows.Media.TextFormatting.TextSource>派生する必要があります。 <xref:System.Windows.Media.TextFormatting.TextSource>テキスト フォーマッタがテキスト ストアからテキスト ランを取得するために使用するメソッドを定義します。 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>は、行の書式設定で使用されるテキスト ランを取得するためにテキスト フォーマッタで使用されるメソッドです。 次のいずれかの条件<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>が発生するまで、テキスト フォーマッタによって呼び出しが繰り返し行われます。  
  
- <xref:System.Windows.Media.TextFormatting.TextEndOfLine>またはサブクラスが返されます。  
  
- テキストランの累積幅が、テキストフォーマッタを作成する呼び出しまたはテキストフォーマッタの<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>メソッドの呼び出しで指定された最大行幅を超えています。  
  
- "CF"、"LF"、または "CRLF" などの Unicode 改行シーケンスが返されます。  
  
<a name="section4"></a>
## <a name="providing-text-runs"></a>テキスト ランを提供する  
 テキスト書式設定プロセスの中心となるものは、テキスト フォーマッタとテキスト ストアの間のやりとりです。 の実装では<xref:System.Windows.Media.TextFormatting.TextSource>、テキスト・フォーマッタに<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトと、テキスト・ランのフォーマットに使用するプロパティーを提供します。 この対話は、テキスト<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>フォーマッタによって呼び出されるメソッドによって処理されます。  
  
 次の表に、定義済みの<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトの一部を示します。  
  
|TextRun の種類|使用法|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|文字グリフの表示をテキスト フォーマッタに返すために使用される特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|テキスト内のボタンやイメージなど、測定、ヒット テスト、描画が全部行われるコンテンツを提供するための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|行の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|段落の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|前<xref:System.Windows.Media.TextFormatting.TextModifier>の実行によって影響を受けるスコープを終了するなど、セグメントの終了をマークするために使用される特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|隠れ文字の範囲をマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|その範囲でテキスト ランのプロパティを変更するための特殊なテキスト ラン。 スコープは、次に一致<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>するテキスト ラン、または<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>次の テキスト ランにまで拡張されます。|  
  
 定義済み<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトは、サブクラス化できます。 それにより、テキスト ソースはテキスト フォーマッタにカスタム データを含むテキスト ランを提供できます。  
  
 メソッドの例を次に<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>示します。 このテキスト ストア<xref:System.Windows.Media.TextFormatting.TextRun>は、処理のためにテキスト フォーマッタにオブジェクトを返します。  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> この例では、テキスト ストアはすべてのテキストに同じテキスト プロパティを提供します。 高度なテキスト ストアでは、場合によっては、独自のスパン管理を実装し、個々の文字に異なるプロパティを与えるようにする必要があります。  
  
<a name="section5"></a>
## <a name="specifying-formatting-properties"></a>書式設定プロパティを指定する  
 <xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトは、テキスト ストアによって提供されるプロパティを使用して書式設定されます。 これらのプロパティには、<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>と の<xref:System.Windows.Media.TextFormatting.TextRunProperties>2 種類があります。 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>などの<xref:System.Windows.TextAlignment>段落包括プロパティを処理<xref:System.Windows.FlowDirection>します。 <xref:System.Windows.Media.TextFormatting.TextRunProperties>は、前景ブラシ<xref:System.Windows.Media.Typeface>、、、フォント サイズなど、段落内で実行されるテキストごとに異なるプロパティです。 カスタムパラグラフおよびカスタム テキスト run プロパティ型を実装するには、アプリケーションで、<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>それぞれ<xref:System.Windows.Media.TextFormatting.TextRunProperties>から派生したクラスを作成する必要があります。  
  
## <a name="see-also"></a>関連項目

- [WPF のタイポグラフィ](typography-in-wpf.md)
- [WPF のドキュメント](documents-in-wpf.md)

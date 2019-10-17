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
ms.openlocfilehash: 2c120c6d71cb22bc38909f980b2f6faf2b5c3663
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395214"
---
# <a name="advanced-text-formatting"></a>テキストの高度な書式設定
Windows Presentation Foundation (WPF) は、アプリケーションにテキストを含めるための堅牢な Api のセットを提供します。 レイアウトと @no__t 0APIs (<xref:System.Windows.Controls.TextBlock> など) は、テキスト表示に最も一般的で一般的な使用要素を提供します。 @No__t-0 や <xref:System.Windows.Media.FormattedText> などの描画 Api は、書式設定されたテキストを描画に含めるための手段を提供します。 最も高度なレベルでは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は拡張テキスト書式設定エンジンを提供し、テキストストア管理、テキストラン書式設定管理、埋め込みオブジェクト管理など、テキスト表示のあらゆる側面を制御します。  
  
 このトピックでは、@no__t テキストの書式設定の概要について説明します。 クライアントの実装と [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] テキスト書式設定エンジンの使用に焦点を当てています。  
  
> [!NOTE]
> このドキュメント内のすべてのコード例は、[高度なテキストの書式設定のサンプル](https://go.microsoft.com/fwlink/?LinkID=159965)に記載されています。  

<a name="prereq"></a>   
## <a name="prerequisites"></a>必要条件  
 このトピックでは、テキスト表示に使用される高レベルの Api について理解していることを前提としています。 ほとんどのユーザーシナリオでは、このトピックで説明する高度なテキスト書式設定 Api は必要ありません。 さまざまなテキスト Api の概要については、「 [WPF のドキュメント](documents-in-wpf.md)」を参照してください。  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 @No__t-1 のテキストレイアウトと @no__t 0 コントロールは、書式設定されたテキストをアプリケーションに簡単に含めることができる書式設定プロパティを提供します。 これらのコントロールでは、テキストの表示を処理するさまざまなプロパティが公開されます。書体、大きさ、色などです。 通常の状況では、これらのコントロールはアプリケーションの大半のテキスト表示を処理できます。 しかしながら、一部の高度なシナリオでは、テキスト表示と同様にテキスト保存を制御する必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、その目的のための拡張テキスト書式設定エンジンを提供します。  
  
 @No__t 0 の高度なテキスト書式設定機能は、テキストの書式設定エンジン、テキストストア、テキストラン、および書式設定のプロパティで構成されています。 テキストの書式設定エンジン (@no__t 0) は、プレゼンテーションに使用されるテキストの行を作成します。 これを実現するには、行の書式設定プロセスを開始し、テキストフォーマッタの <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> を呼び出します。 テキストフォーマッタは、ストアの @no__t 0 メソッドを呼び出すことによって、テキストストアからテキストランを取得します。 次に、@no__t 0 のオブジェクトがテキストフォーマッタによって @no__t 1 のオブジェクトに変換され、検査または表示のためにアプリケーションに渡されます。  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>テキスト フォーマッタを使用する  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> は [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] テキスト書式設定エンジンであり、テキスト行の書式設定と区切りを行うためのサービスを提供します。 テキスト フォーマッタは、さまざまなテキスト文字書式や段落スタイルを処理し、国際的なテキスト レイアウトに対応しています。  
  
 従来のテキスト API とは異なり、<xref:System.Windows.Media.TextFormatting.TextFormatter> は、一連のコールバックメソッドを使用してテキストレイアウトクライアントと対話します。 クライアントは、@no__t 0 クラスの実装でこれらのメソッドを提供する必要があります。 次の図は、クライアントアプリケーションと <xref:System.Windows.Media.TextFormatting.TextFormatter> の間のテキストレイアウトの相互作用を示しています。  
  
 ![テキスト レイアウト クライアントと TextFormatter のダイアグラム](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 テキストフォーマッタは、<xref:System.Windows.Media.TextFormatting.TextSource> の実装であるテキストストアから書式設定されたテキスト行を取得するために使用されます。 これを行うには、最初に <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> メソッドを使用してテキストフォーマッタのインスタンスを作成します。 このメソッドはテキスト フォーマッタのインスタンスを作成し、行の高さと幅の最大値を設定します。 テキストフォーマッタのインスタンスが作成されるとすぐに、<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> メソッドを呼び出すことによって、行の作成プロセスが開始されます。 <xref:System.Windows.Media.TextFormatting.TextFormatter> はテキストソースにコールバックして、テキストを取得し、行を形成するテキストの実行に関するパラメーターを書式設定します。  
  
 次の例は、テキスト ストアを書式設定するプロセスを示しています。 @No__t-0 オブジェクトを使用してテキストストアからテキスト行を取得し、<xref:System.Windows.Media.DrawingContext> に描画するためのテキスト行を書式設定します。  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>クライアント テキスト ストアを実装する  
 テキスト書式設定エンジンを拡張するとき、テキスト ストアのあらゆる側面を実装し、管理する必要があります。 これは簡単な作業ではありません。 テキスト ストアは、テキスト ランのプロパティ、段落のプロパティ、埋め込みオブジェクト、その他の同様のコンテンツの追跡を担当します。 また、テキストフォーマッタには、テキストフォーマッタが <xref:System.Windows.Media.TextFormatting.TextLine> オブジェクトを作成するために使用する個々の @no__t 0 オブジェクトを指定します。  
  
 テキストストアの仮想化を処理するには、テキストストアを <xref:System.Windows.Media.TextFormatting.TextSource> から派生させる必要があります。 <xref:System.Windows.Media.TextFormatting.TextSource> テキストストアからテキストランを取得するためにテキストフォーマッタが使用するメソッドを定義します。 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> は、テキストフォーマッタが行の書式設定で使用されるテキストランを取得するために使用するメソッドです。 @No__t-0 の呼び出しは、次のいずれかの条件が発生するまで、テキストフォーマッタによって繰り返し行われます。  
  
- @No__t 0 またはサブクラスが返されます。  
  
- テキストランの累積幅が、テキストフォーマッタを作成するための呼び出し、またはテキストフォーマッタの <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> メソッドの呼び出しで指定された最大線幅を超えています。  
  
- "CF"、"LF"、"CRLF" などの Unicode 改行シーケンスが返されます。  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>テキスト ランを提供する  
 テキスト書式設定プロセスの中心となるものは、テキスト フォーマッタとテキスト ストアの間のやりとりです。 @No__t-0 の実装では、テキストフォーマッタに @no__t 1 つのオブジェクトと、テキストランの書式設定に使用するプロパティが用意されています。 この相互作用は、テキストフォーマッタによって呼び出される <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> メソッドによって処理されます。  
  
 次の表は、定義済みの @no__t 0 オブジェクトの一部を示しています。  
  
|TextRun の種類|使用方法|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|文字グリフの表示をテキスト フォーマッタに返すために使用される特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|テキスト内のボタンやイメージなど、測定、ヒット テスト、描画が全部行われるコンテンツを提供するための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|行の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|段落の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|セグメントの末尾を示すために使用される特殊なテキストラン。たとえば、前の <xref:System.Windows.Media.TextFormatting.TextModifier> 実行の影響を受けるスコープを終了するように指定します。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|隠れ文字の範囲をマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|その範囲でテキスト ランのプロパティを変更するための特殊なテキスト ラン。 スコープは、次に一致する <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> テキストラン、または次の <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph> までとなります。|  
  
 定義済みの @no__t 0 オブジェクトのいずれかをサブクラス化できます。 それにより、テキスト ソースはテキスト フォーマッタにカスタム データを含むテキスト ランを提供できます。  
  
 次の例は、@no__t 0 のメソッドを示しています。 このテキストストアは、処理のためにテキストフォーマッタに @no__t 0 のオブジェクトを返します。  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> この例では、テキスト ストアはすべてのテキストに同じテキスト プロパティを提供します。 高度なテキスト ストアでは、場合によっては、独自のスパン管理を実装し、個々の文字に異なるプロパティを与えるようにする必要があります。  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>書式設定プロパティを指定する  
 @no__t 0 のオブジェクトは、テキストストアによって提供されるプロパティを使用して書式設定されます。 これらのプロパティには、@no__t 0 と <xref:System.Windows.Media.TextFormatting.TextRunProperties> の2種類があります。 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> <xref:System.Windows.TextAlignment>、<xref:System.Windows.FlowDirection> などの段落包括プロパティを処理します。 <xref:System.Windows.Media.TextFormatting.TextRunProperties> は、前景ブラシ、<xref:System.Windows.Media.Typeface>、フォントサイズなど、段落内の各テキストランで異なる可能性があるプロパティです。 カスタムの段落およびカスタムテキスト実行プロパティの型を実装するには、アプリケーションで <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> から派生し、<xref:System.Windows.Media.TextFormatting.TextRunProperties> のクラスを作成する必要があります。  
  
## <a name="see-also"></a>関連項目

- [WPF のタイポグラフィ](typography-in-wpf.md)
- [WPF のドキュメント](documents-in-wpf.md)

---
title: TextPattern および埋め込みオブジェクトの概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: c8dc4ba5a17ca6a950d7ef3e0835f31463979bd3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342519"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern および埋め込みオブジェクトの概要
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 この概要では、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] がテキスト ドキュメントまたはコンテナー内で埋め込みオブジェクトや子要素を公開する方法について説明します。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、埋め込みオブジェクトは、テキスト以外の境界を持つ任意の要素です。たとえば、イメージ、ハイパーリンク、テーブル、ドキュメントの種類 ( [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] スプレッドシートや [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] ファイルなど) があります。 これは、あるアプリケーションで要素が作成され、別のアプリケーション内に埋め込まれる (リンクされる) 標準的な定義とは異なります。 オブジェクトを元のアプリケーション内で編集できるかどうかは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の状況とは無関係です。  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>埋め込みオブジェクトと UI オートメーション ツリー  
 埋め込みオブジェクトは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビュー内では個々の要素として扱われます。 これらはテキスト コンテナーの子として公開され、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の他のコントロールと同じモデルを介してアクセスできます。  
  
 ![テキスト コンテナー内のイメージを含むテーブルを埋め込む](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
テーブル、イメージ、ハイパーリンクの埋め込みオブジェクトを含むテキスト コンテナーの例  
  
 ![上記の例では、ビューのコンテンツ](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
前のテキスト コンテナーの一部のコンテンツ ビューの例  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>TextPattern と TextPatternRange を使用した埋め込みオブジェクトの公開  
 <xref:System.Windows.Automation.TextPattern> コントロール パターン クラスと <xref:System.Windows.Automation.Text.TextPatternRange> クラスを組み合わせて使用すると、埋め込みオブジェクトのナビゲーションと照会を容易にするメソッドとプロパティが公開されます。  
  
 テキスト コンテナーのテキスト コンテンツ (内部テキスト) と埋め込みオブジェクト (ハイパーリンクやテーブルのセルなど) は、連続する単一のテキスト ストリームとして、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューの両方で公開されます。そのため、オブジェクトの境界は無視されます。 UI オートメーション クライアントがなんらかの方法で列挙、解釈、分析を目的としてテキストを取得している場合、テキスト コンテンツを含むテーブルやその他の埋め込みオブジェクトなど、特殊なケースについて、テキスト範囲を確認する必要があります。 これを行うには、 <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> を呼び出して各埋め込みオブジェクトの <xref:System.Windows.Automation.AutomationElement> を取得した後、 <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> を呼び出して各要素のテキスト範囲を取得します。 この操作は、すべてのテキスト コンテンツが取得されるまで再帰的に行われます。  
  
 ![埋め込みオブジェクトにまたがるテキスト範囲。](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
埋め込みオブジェクトとその範囲を含むテキスト ストリームの例  
  
 テキスト範囲の内容を走査する必要がある場合、 <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> メソッドを正常に実行するために、一連の手順がその背後で関係しています。  
  
1. テキスト範囲は正規化されます。つまり、テキスト範囲は <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> エンドポイントで低次元テキスト範囲に縮小されるため、 <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> エンドポイントは不要になります。 この手順は、テキスト範囲にまたがる状況であいまいさをなくすために必要<xref:System.Windows.Automation.Text.TextUnit>境界: たとえば、`{The URL https://www.microsoft.com is embedded in text`場所"{0}"と"}"がテキスト範囲エンドポイント。  
  
2. 結果として得られる範囲は、 <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> 内で、要求された <xref:System.Windows.Automation.Text.TextUnit> 境界の先頭に向かって後方に移動されます。  
  
3. この範囲は、 <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> 内で、 <xref:System.Windows.Automation.Text.TextUnit> 境界の要求された数だけ、前方または後方に移動されます。  
  
4. その後、この範囲は、要求された 1 つの <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> 境界の分、 <xref:System.Windows.Automation.Text.TextUnit> エンドポイントを移動することによって、低次元テキスト範囲の状態から展開されます。  
  
 ![Move & ExpandToEnclosingUnit による範囲調整](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
テキスト範囲を Move() と ExpandToEnclosingUnit() に対して調整する方法の例  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>一般的なシナリオ  
 以下のセクションでは、埋め込みオブジェクトが関連する最も一般的なシナリオの例を紹介します。  
  
 この例で使用される凡例は次のとおりです。  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>ハイパーリンク  

**例 1: 埋め込みテキスト ハイパーリンクを含むテキスト範囲**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|呼び出されるメソッド|結果|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|文字列 `The URL https://www.microsoft.com is embedded in text` を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|テキスト範囲を囲む最も内側の <xref:System.Windows.Automation.AutomationElement> を返します。この場合は、テキスト プロバイダー自体を表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|ハイパーリンク コントロールを表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> ( <xref:System.Windows.Automation.AutomationElement> は、前の `GetChildren` メソッドから返されるオブジェクト)|範囲を表すを返します"https://www.microsoft.com"。|  
  
 **例 2: 埋め込みテキスト ハイパーリンクに部分的にかかるテキスト範囲**  
  
 URL`https://{[www]}`はテキストに埋め込まれます。  
  
|呼び出されるメソッド|結果|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|文字列 "www" を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|テキスト範囲を囲む最も内側の <xref:System.Windows.Automation.AutomationElement> を返します。この場合は、ハイパーリンク コントロールです。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|テキスト範囲が URL 文字列全体をカバーしていないため、 `null` を返します。|  
  
**例 3 - テキスト コンテナーのコンテンツを部分的にまたがるテキスト範囲。テキスト コンテナーには、テキスト範囲の一部ではない埋め込みテキスト ハイパーリンクがあります。**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|呼び出されるメソッド|結果|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|文字列 "The URL" を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|テキスト範囲を囲む最も内側の <xref:System.Windows.Automation.AutomationElement> を返します。この場合は、テキスト プロバイダー自体を表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (パラメーターは (TextUnit.Word, 1))|ハイパーリンクのテキストは個々の単語で構成されているため、テキスト範囲は "http" に移動します。 この場合、ハイパーリンクは 1 つのオブジェクトとして扱われません。<br /><br /> URL {0} [http]} は、テキストに埋め込まれます。|  
  
<a name="Image"></a>   
### <a name="image"></a>イメージ  
 **例 1: 埋め込みイメージを含むテキスト範囲**  
  
 {0} イメージ![埋め込みイメージの例](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")テキストに埋め込まれた}。  
  
|呼び出されるメソッド|結果|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|文字列 "The is embedded in text" を返します。 イメージに関連付けられた代替テキストがテキスト ストリームに含まれることはありません。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|テキスト範囲を囲む最も内側の <xref:System.Windows.Automation.AutomationElement> を返します。この場合は、テキスト プロバイダー自体を表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|イメージ コントロールを表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> ( <xref:System.Windows.Automation.AutomationElement> は、前の <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> メソッドから返されるオブジェクト)|表す低次元テキスト範囲を返します"![埋め込みイメージ例](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")"。|  
  
 **例 2: テキスト コンテナーのコンテンツを部分的にまたがるテキスト範囲。テキスト コンテナーは、埋め込み画像、テキスト範囲の一部ではないです。**  
  
 {0} イメージ}![埋め込みイメージ例](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")はテキストに埋め込まれます。  
  
|呼び出されるメソッド|結果|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|文字列 "The image" を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|テキスト範囲を囲む最も内側の <xref:System.Windows.Automation.AutomationElement> を返します。この場合は、テキスト プロバイダー自体を表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (パラメーターは (TextUnit.Word, 1))|テキスト範囲は "is " に移動します。 テキスト ベースの埋め込みオブジェクトのみがテキスト ストリームの一部と見なされるため、この例のイメージは Move やその戻り値 (この場合は 1) に影響を与えません。|  
  
<a name="Table"></a>   
### <a name="table"></a>テーブル  
  
### <a name="table-used-for-examples"></a>例で使用するテーブル  
  
|イメージを含むセル|テキストを含むセル|  
|---------------------|--------------------|  
|![イメージの例の埋め込み](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|x|  
|![埋め込み画像の例 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Y|  
|![イメージの例 3 を埋め込み](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Z のイメージ|Z|  
  
 **例 1: セルのコンテンツからテキスト コンテナーを取得する**  
  
|呼び出されるメソッド|結果|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> (パラメーターは (0, 0))|セルのコンテンツを表す <xref:System.Windows.Automation.AutomationElement> を返します。この場合、要素はテキスト コントロールです。|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> ( <xref:System.Windows.Automation.AutomationElement> は、前の `GetItem` メソッドから返されるオブジェクト)|イメージをカバーする範囲を返します![埋め込みイメージ例](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")します。|  
|前の<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> メソッドから返されるオブジェクトの `RangeFromChild` |セルを表す <xref:System.Windows.Automation.AutomationElement> を返します。この場合、要素は TableItemPattern をサポートするテキスト コントロールです。|  
|前の<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> メソッドから返されるオブジェクトの `GetEnclosingElement` |テーブルを表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
|前の<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> メソッドから返されるオブジェクトの `GetEnclosingElement` |テキスト プロバイダー自体を表す <xref:System.Windows.Automation.AutomationElement> を返します。|  
  
 **例 2: セルのテキスト コンテンツを取得する**  
  
|呼び出されるメソッド|結果|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> (パラメーターは (1, 1))|セルのコンテンツを表す <xref:System.Windows.Automation.AutomationElement> を返します。この場合、要素はテキスト コントロールです。|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> ( <xref:System.Windows.Automation.AutomationElement> は、前の `GetItem` メソッドから返されるオブジェクト)|"Y" を返します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [UI オートメーションを使用した、埋め込みオブジェクトへのアクセス](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)
- [UI オートメーションを使用したテーブルの内容の公開](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)
- [UI オートメーションを使用したテキストのスキャン](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)
- [TextPattern の検索と選択のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)

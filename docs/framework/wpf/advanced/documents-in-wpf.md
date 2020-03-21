---
title: Documents
ms.date: 03/30/2017
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
ms.openlocfilehash: e88604c42b253b48ee605f42f24fe301e339f74b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174681"
---
# <a name="documents-in-wpf"></a>WPF のドキュメント
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、以前の世代の Windows よりも簡単にアクセスおよび読み取りができるように設計された、忠実度の高いコンテンツの作成を可能にする、さまざまなドキュメント機能を提供します。 拡張された機能と品質に加えて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ドキュメントの表示、パッケージ化、およびセキュリティの統合されたサービスも提供します。 ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のドキュメントの種類とドキュメントのパッケージ化の概要を説明します。  

<a name="types_of_documents"></a>
## <a name="types-of-documents"></a>ドキュメントの種類  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ドキュメントは用途に基づいて大きく 2 つのカテゴリに分けられます。これらのドキュメントのカテゴリは "固定ドキュメント" および "フロー ドキュメント" と呼ばれます。  
  
 固定ドキュメントは、使用するディスプレイやプリンタハードウェアに関係なく、正確な「表示内容が何を得られるか」(WYSIWYG)プレゼンテーションを必要とするアプリケーションを対象としています。 固定ドキュメントの一般的な用途としては、元のページ デザインに準拠していることが重要になるデスクトップ パブリッシング、ワード プロセッシング、およびフォーム レイアウトなどがあります。 レイアウトの一部として、固定ドキュメントでは、使用中のディスプレイまたは印刷デバイスに依存しないコンテンツ要素の正確な配置位置が保持されます。 たとえば、96 dpi のディスプレイに表示される固定ドキュメント ページは、600 dpi のレーザー プリンターに出力される場合に、4800 dpi の写真植字に出力される場合とまったく同じように表示されます。 ドキュメントの品質は各デバイスの機能に応じて最大化されますが、ページ レイアウトはすべての場合において同じになります。  
  
 これに対して、フロー ドキュメントは、表示と読みやすさを最適化するように設計されており、ドキュメントが主に読みやすさを目的としている場合に最適です。 フロー ドキュメントは、1 つの定義済みのレイアウトに設定するのではなく、ウィンドウのサイズ、デバイスの解像度、省略可能なユーザー設定など、ランタイム変数に基づいてコンテンツを動的に調整したりリフローしたりします。 Web ページは、そのコンテンツが現在のウィンドウに収まるように動的にフォーマットされるフロー ドキュメントの簡単な例です。 フロー ドキュメントは、ランタイム環境に基づいて、ユーザーにとっての表示と読みやすさを最適化します。 たとえば、同じフロー ドキュメントでも、高解像度の 19 インチ ディスプレイなのか、小型の 2x3 インチの PDA 画面なのかに応じて、最も読みやすくなるように書式設定が動的に変更されます。 また、フロー ドキュメントには、検索、読みやすさを最適化するモードの表示、およびフォントのサイズと外観を変更する機能を含むさまざまな組み込み機能があります。  フロー ドキュメントの図、例、および詳細については、「[フロー ドキュメントの概要](flow-document-overview.md)」を参照してください。  
  
<a name="document_viewer"></a>
## <a name="document-controls-and-text-layout"></a>ドキュメント コントロールとテキスト レイアウト  
 .NET Framework には、アプリケーション内で固定ドキュメント、フロー ドキュメント、および一般的なテキストを簡単に使用できる、あらかじめ組み込まれたコントロールのセットが用意されています。  コントロールを使用して、固定ドキュメントコンテンツの表示<xref:System.Windows.Controls.DocumentViewer>がサポートされます。  フロー ドキュメントコンテンツの表示は、 <xref:System.Windows.Controls.FlowDocumentReader>、、<xref:System.Windows.Controls.FlowDocumentPageViewer>ユーザー<xref:System.Windows.Controls.FlowDocumentScrollViewer>シナリオに対応する 3 つのコントロールによってサポートされます (以下のセクションを参照)。  その他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールでは、一般的なテキストの使用をサポートする簡略化されたレイアウトが提供されます (後述の「[ユーザー インターフェイスのテキスト](#text_in_the_user_interface)」を参照してください)。  
  
### <a name="fixed-document-control---documentviewer"></a>固定ドキュメント コントロール - DocumentViewer  
 コントロール<xref:System.Windows.Controls.DocumentViewer>は、コンテンツを表示<xref:System.Windows.Documents.FixedDocument>するように設計されています。 この<xref:System.Windows.Controls.DocumentViewer>コントロールは、印刷出力、クリップボードへのコピー、ズーム、テキスト検索機能などの一般的な操作をサポートする直感的なユーザー インターフェイスを提供します。 コントロールは、使い慣れたスクロール機構を使用してコンテンツのページへのアクセスを提供します。 すべての[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールと同様<xref:System.Windows.Controls.DocumentViewer>に、完全または部分的な再スタイル設定をサポートし、コントロールを実質的にあらゆるアプリケーションや環境に視覚的に統合できます。  
  
 <xref:System.Windows.Controls.DocumentViewer>コンテンツを読み取り専用で表示するように設計されています。コンテンツの編集や変更は利用できず、サポートされていません。  
  
<a name="flow_document"></a>
### <a name="flow-document-controls"></a>フロー ドキュメント コントロール  

> [!NOTE]
> フロードキュメント機能の詳細と作成方法については、[フロードキュメントの概要](flow-document-overview.md)を参照してください。  
  
 フロー ドキュメントコンテンツの表示は、 <xref:System.Windows.Controls.FlowDocumentReader>、 、<xref:System.Windows.Controls.FlowDocumentPageViewer>および<xref:System.Windows.Controls.FlowDocumentScrollViewer>の 3 つのコントロールによってサポートされます。  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>ユーザーが、1 ページ (一度にページ) 表示モード、2 ページ/時刻 (書籍の読み取り形式) 表示モード、連続スクロール (ボトムレス) 表示モードなど、さまざまな表示モードを動的に選択できる機能が含まれています。  これらの表示モードの詳細については、を参照<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>してください。  異なる表示モードを動的に切り替える機能が不要で<xref:System.Windows.Controls.FlowDocumentPageViewer><xref:System.Windows.Controls.FlowDocumentScrollViewer>、特定の表示モードで固定されている、より軽量なフロー コンテンツ ビューアーを提供する必要がない場合。  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer と FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>は、連続スクロール モードでコンテンツを表示しながら<xref:System.Windows.Controls.FlowDocumentScrollViewer>、一度にページ表示モードでコンテンツを表示します。  両方<xref:System.Windows.Controls.FlowDocumentPageViewer>とも<xref:System.Windows.Controls.FlowDocumentScrollViewer>特定の表示モードに固定されています。 Compare<xref:System.Windows.Controls.FlowDocumentReader>と比較すると、ユーザーがさまざまな表示モード (<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>列挙によって<xref:System.Windows.Controls.FlowDocumentPageViewer>提供される) 間で動的に選択できる機能が含まれています。 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
  
 既定では、垂直スクロール バーは常に表示され、水平スクロール バーは必要に応じて表示されます。 の<xref:System.Windows.Controls.FlowDocumentScrollViewer>デフォルト[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]にはツールバーは含まれていません。ただし、この<xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A>プロパティを使用して、組み込みのツール バーを有効にできます。  
  
<a name="text_in_the_user_interface"></a>
### <a name="text-in-the-user-interface"></a>ユーザー インターフェイスのテキスト  
 ドキュメントへのテキストの追加だけでなく、テキストはもちろん、フォームなどのアプリケーション UI で使用できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、画面にテキストを描画するための複数のコントロールが含まれています。 各コントロールは異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。 一般に<xref:System.Windows.Controls.TextBlock>、この要素は、テキストサポートが限定されている場合 (短い文など)[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]で使用する必要があります。 <xref:System.Windows.Controls.Label>最小限のテキストサポートが必要な場合に使用できます。 詳細については、「[TextBlock の概要](../controls/textblock-overview.md)」を参照してください。  
  
<a name="packaging"></a>
## <a name="document-packaging"></a>ドキュメントのパッケージ化  
 この<xref:System.IO.Packaging>API は、アプリケーション データ、ドキュメント コンテンツ、および関連リソースを、簡単にアクセスでき、移植性が高く、配布しやすい単一のコンテナーに整理するための効率的な手段を提供します。 ZIP ファイルは、複数のオブジェクト<xref:System.IO.Packaging.Package>を 1 つの単位として保持できる型の例です。 パッケージ API は、XML<xref:System.IO.Packaging.ZipPackage>および ZIP ファイル アーキテクチャを使用したオープン パッケージ化規則標準を使用して設計された既定の実装を提供します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]パッケージ API を使用すると、パッケージを作成し、パッケージ内にオブジェクトを格納してアクセスすることが簡単になります。 に格納されたオブジェクト<xref:System.IO.Packaging.Package>は<xref:System.IO.Packaging.PackagePart>、("part")と呼ばれます。 パッケージには、パーツの発行元を識別し、パッケージのコンテンツが変更されていないことを検証するのに使用できる署名されたデジタル証明書を含めることもできます。  パッケージには、既存<xref:System.IO.Packaging.PackageRelationship>のパーツのコンテンツを実際に変更することなく、パッケージに追加したり、特定のパーツに関連付けたりできる機能も含まれています。  パッケージ サービスは、マイクロソフトの Windows 権利管理 (RM) もサポートします。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パッケージ アーキテクチャは、さまざまな重要な技術の基盤として機能します。  
  
- XML 用紙仕様 (XPS) に準拠した XPS ドキュメント。  
  
- Microsoft Office "12" Open XML 形式のドキュメント (.docx)。  
  
- 独自のアプリケーション設計のカスタム保存形式。  
  
 パッケージ化 API に基づいて<xref:System.Windows.Xps.Packaging.XpsDocument>、 は、フィックス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]・コンテンツ文書を保管するために特別に設計されています。 は<xref:System.Windows.Xps.Packaging.XpsDocument>、ビューアーで開いたり、<xref:System.Windows.Controls.DocumentViewer>コントロールに表示したり、印刷スプールにルーティングしたり、XPS 互換プリンターに直接出力したりできる、自己完結型のドキュメントです。  
  
 以下のセクションでは、 で提供<xref:System.IO.Packaging.Package>される<xref:System.Windows.Xps.Packaging.XpsDocument>API および[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API に関する追加情報を提供します。  
  
<a name="packages"></a>
### <a name="package-components"></a>パッケージ コンポーネント  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パッケージ化 API は、アプリケーション データとドキュメントを 1 つの移植可能な単位に編成できるようにします。 ZIP ファイルは、最もよく使用されるパッケージの種類の 1 つであり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で用意されている既定のパッケージの種類です。  <xref:System.IO.Packaging.Package>それ自体は、オープン標準の<xref:System.IO.Packaging.ZipPackage>XMLとZIPファイルアーキテクチャを使用して実装される抽象クラスです。  この<xref:System.IO.Packaging.Package.Open%2A>メソッドは<xref:System.IO.Packaging.ZipPackage>、デフォルトで ZIP ファイルを作成して使用するために使用します。 パッケージには、次の 3 種類の基本的な項目を含めることができます。  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|アプリケーション コンテンツ、データ、ドキュメント、およびリソース ファイル。|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|識別、認証、および検証のための [X.509 証明書]。|  
|<xref:System.IO.Packaging.PackageRelationship>|パッケージまたは特定のパーツに関連する追加された情報。|  
  
<a name="PackageParts"></a>
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> (「パーツ」) は、 に格納されているオブジェクトを参照する抽象<xref:System.IO.Packaging.Package>クラスです。 ZIP ファイルでは、パッケージ パーツは ZIP ファイル内に格納された個別のファイルに対応します。  <xref:System.IO.Packaging.ZipPackagePart>には、シリアル化可能なオブジェクトの既定の実装<xref:System.IO.Packaging.ZipPackage>が用意されています。  ファイル システムと同様に、パッケージに含まれているパーツは、階層的ディレクトリまたは "フォルダー スタイル" 編成で格納されます。  パッケージ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API を使用すると、アプリケーションは単一の ZIP<xref:System.IO.Packaging.PackagePart>ファイル コンテナーを使用して複数のオブジェクトを書き込み、格納、および読み取ることができます。  
  
<a name="PackageDigitalSignatures"></a>
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 セキュリティ上、パッケージ<xref:System.IO.Packaging.PackageDigitalSignature>内のパーツに関連付けることができます(「デジタル署名」)。 A<xref:System.IO.Packaging.PackageDigitalSignature>には、次の 2 つの機能を提供する [509] が組み込まれています。  
  
1. パーツの発行元を識別および認証します。  
  
2. パーツが変更されていないことを検証します。  
  
 デジタル署名はパーツを変更できなくするものではありませんが、パーツが何らかの方法で変更されている場合、デジタル署名に対する検証チェックは失敗します。 その後、アプリケーションでは適切なアクションを実行することができます。たとえば、パーツを開く操作をブロックしたり、パーツが変更されていて安全ではないことをユーザーに知らせたりすることができます。  
  
<a name="PackageRelationships"></a>
#### <a name="packagerelationships"></a>PackageRelationships  
 (「<xref:System.IO.Packaging.PackageRelationship>関係」) は、パッケージまたはパッケージ内の部品に追加情報を関連付けるメカニズムを提供します。 リレーションシップは、実際のパーツのコンテンツを変更することなく追加情報をパーツに関連付けることができるパッケージ レベルの機能です。 パーツのコンテンツに新しいデータを直接挿入するのは、次のように多くの場合において実用的ではありません。  
  
- パーツの実際の種類およびそのコンテンツ スキーマが不明な場合。  
  
- わかっている場合でも、コンテンツ スキーマが新しい情報を追加する方法を提供しない可能性がある場合。  
  
- パーツが、デジタル署名されたり、暗号化されたり、変更できなくされたりする可能性がある場合。  
  
 パッケージ リレーションシップは、追加情報を個別のパーツまたはパッケージ全体に追加または関連付けるための検出可能な方法を提供します。 パッケージ リレーションシップは、次の 2 つの主要な機能のために使用されます。  
  
1. 1 つのパーツから別のパーツへの依存関係の定義。  
  
2. メモまたはパーツに関連したその他のデータを追加する情報リレーションシップの定義。  
  
 A<xref:System.IO.Packaging.PackageRelationship>は、依存関係を定義し、パッケージまたはパッケージ全体の一部に関連するその他の情報を追加するための、迅速かつ検出可能な手段を提供します。  
  
<a name="Dependency_Relationships"></a>
##### <a name="dependency-relationships"></a>依存関係  
 依存関係は、1 つのパーツによって他のパーツに対して作成される依存関係を記述するために使用されます。 たとえば、パッケージには、1 つ以上の \<img> イメージ タグを含む HTML パーツが含まれている場合があります。 イメージ タグは、パッケージの内部またはパッケージの外部 (インターネット経由でアクセスできる場合など) にあるその他のパーツとして配置されているイメージを参照します。 HTML<xref:System.IO.Packaging.PackageRelationship>ファイルに関連付けられたを作成すると、依存リソースの検出とアクセスが迅速かつ容易になります。 ブラウザーまたはビューアー アプリケーションは、パーツ リレーションシップに直接アクセスし、スキーマが不明である場合や、ドキュメントの解析を行わない状態でも依存リソースをすぐにアセンブルできます。  
  
<a name="Information_Relationships"></a>
##### <a name="information-relationships"></a>情報リレーションシップ  
 注記や注釈と同様に、部品<xref:System.IO.Packaging.PackageRelationship>コンテンツ自体を実際に修正することなく、部品に関連付ける他のタイプの情報を保存することもできます。  
  
<a name="XPS_Documents"></a>
## <a name="xps-documents"></a>XPS ドキュメント  
 XML 用紙仕様 (XPS) ドキュメントは、1 つ以上の固定ドキュメントと、レンダリングに必要なすべてのリソースと情報を含むパッケージです。  XPS は、Windows Vista のネイティブ印刷スプール ファイル形式でもあります。  は<xref:System.Windows.Xps.Packaging.XpsDocument>標準の ZIP データセットに格納され、XML とバイナリ コンポーネント (イメージファイルやフォント ファイルなど) の組み合わせを含めることができます。 [PackageRelationships](#PackageRelationships) は、ドキュメントを完全にレンダリングするために必要なコンテンツとリソースの間の依存関係を定義するために使用されます。  この<xref:System.Windows.Xps.Packaging.XpsDocument>設計は、複数の用途をサポートする、1 つの高忠実度ドキュメント ソリューションを提供します。  
  
- 単一の移植可能で配布しやすいファイルとして、固定ドキュメント コンテンツおよびリソースを読み取り、書き込み、および格納する。  
  
- XPS ビューア アプリケーションでドキュメントを表示する。  
  
- Windows Vista のネイティブ印刷スプール出力形式でドキュメントを出力します。  
  
- XPS 互換プリンタにドキュメントを直接ルーティングする。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [テキスト](optimizing-performance-text.md)
- [フロー ドキュメントの概要](flow-document-overview.md)
- [印刷の概要](printing-overview.md)
- [ドキュメントのシリアル化と保存](document-serialization-and-storage.md)

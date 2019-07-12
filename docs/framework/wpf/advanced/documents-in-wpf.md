---
title: WPF のドキュメント
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
ms.openlocfilehash: b83d9c972dbdadb721bae8b7d616c94a0c1c831f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804739"
---
# <a name="documents-in-wpf"></a>WPF のドキュメント
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] の前の世代よりも簡単にアクセスおよび読み取りを行うことができるように設計されている、高品質なコンテンツの作成を可能にするさまざまなドキュメント機能を提供します。 拡張された機能と品質に加えて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ドキュメントの表示、パッケージ化、およびセキュリティの統合されたサービスも提供します。 ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のドキュメントの種類とドキュメントのパッケージ化の概要を説明します。  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>ドキュメントの種類  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ドキュメントは用途に基づいて大きく 2 つのカテゴリに分けられます。これらのドキュメントのカテゴリは "固定ドキュメント" および "フロー ドキュメント" と呼ばれます。  
  
 固定ドキュメントは、使用されるディスプレイまたはプリンター ハードウェアに関係なく、正確な [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] プレゼンテーションを必要とするアプリケーションを対象に用意されています。 固定ドキュメントの一般的な用途としては、元のページ デザインに準拠していることが重要になるデスクトップ パブリッシング、ワード プロセッシング、およびフォーム レイアウトなどがあります。 レイアウトの一部として、固定ドキュメントでは、使用中のディスプレイまたは印刷デバイスに依存しないコンテンツ要素の正確な配置位置が保持されます。 たとえば、96 dpi のディスプレイに表示される固定ドキュメント ページは、600 dpi のレーザー プリンターに出力される場合に、4800 dpi の写真植字に出力される場合とまったく同じように表示されます。 ドキュメントの品質は各デバイスの機能に応じて最大化されますが、ページ レイアウトはすべての場合において同じになります。  
  
 これに対して、フロー ドキュメントは、表示と読みやすさを最適化するように設計されており、ドキュメントが主に読みやすさを目的としている場合に最適です。 フロー ドキュメントは、1 つの定義済みのレイアウトに設定するのではなく、ウィンドウのサイズ、デバイスの解像度、省略可能なユーザー設定など、ランタイム変数に基づいてコンテンツを動的に調整したりリフローしたりします。 Web ページは、そのコンテンツが現在のウィンドウに収まるように動的にフォーマットされるフロー ドキュメントの簡単な例です。 フロー ドキュメントは、ランタイム環境に基づいて、ユーザーにとっての表示と読みやすさを最適化します。 たとえば、同じフロー ドキュメントでも、高解像度の 19 インチ ディスプレイなのか、小型の 2x3 インチの PDA 画面なのかに応じて、最も読みやすくなるように書式設定が動的に変更されます。 また、フロー ドキュメントには、検索、読みやすさを最適化するモードの表示、およびフォントのサイズと外観を変更する機能を含むさまざまな組み込み機能があります。  フロー ドキュメントの図、例、および詳細については、「[フロー ドキュメントの概要](flow-document-overview.md)」を参照してください。  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>ドキュメント コントロールとテキスト レイアウト  
 .NET Framework では、固定ドキュメント、フロー ドキュメント、およびアプリケーション内での一般的なテキストを使用して簡略化する構築済みのコントロールのセットを提供します。  使用して固定ドキュメント コンテンツの表示をサポート、<xref:System.Windows.Controls.DocumentViewer>コントロール。  フロー ドキュメント コンテンツの表示が次の 3 つの異なるコントロールでサポートされて: <xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、および<xref:System.Windows.Controls.FlowDocumentScrollViewer>(以下のセクションを参照してください)、別のユーザー シナリオに割り当てられています。  その他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールでは、一般的なテキストの使用をサポートする簡略化されたレイアウトが提供されます (後述の「[ユーザー インターフェイスのテキスト](#text_in_the_user_interface)」を参照してください)。  
  
### <a name="fixed-document-control---documentviewer"></a>固定ドキュメント コントロール - DocumentViewer  
 <xref:System.Windows.Controls.DocumentViewer>を表示するコントロールがデザインされた<xref:System.Windows.Documents.FixedDocument>コンテンツ。 <xref:System.Windows.Controls.DocumentViewer>コントロールが印刷の出力などの一般的な操作は、クリップボード、ズーム、およびテキストの検索機能をコピーするために、組み込みのサポートを提供直感的なユーザー インターフェイスを提供します。 コントロールは、使い慣れたスクロール機構を使用してコンテンツのページへのアクセスを提供します。 などのすべて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール、<xref:System.Windows.Controls.DocumentViewer>完全または部分的なスタイルの変更をサポートしているほぼすべてのアプリケーションまたは環境に統合する視覚的に制御できます。  
  
 <xref:System.Windows.Controls.DocumentViewer> 読み取り専用の方法でコンテンツを表示するのには設計されています編集またはコンテンツの変更をご利用いただけません、サポートされていません。  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>フロー ドキュメント コントロール  

> [!NOTE]
>  フロー ドキュメント機能とその作成方法について詳細を参照してください。[フロー ドキュメントの概要](flow-document-overview.md)します。  
  
 フロー ドキュメント コンテンツの表示が次の 3 つのコントロールでサポートされる: <xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、および<xref:System.Windows.Controls.FlowDocumentScrollViewer>します。  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> 単一ページ (ページに-、-時に) 表示モード、2 つのページ-で-、-時間 (読書形式) 表示モード、連続したスクロール (ボトムレス) 表示モードなど、各種の表示モードの間で動的に選択するユーザーを有効にする機能が含まれています。  これらの表示モードの詳細については、次を参照してください。<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>します。  さまざまな表示モードを動的に切り替える機能が必要ない場合<xref:System.Windows.Controls.FlowDocumentPageViewer>と<xref:System.Windows.Controls.FlowDocumentScrollViewer>コンテンツ ビューアーは、特定の表示モードで修正される軽量のフローを提供します。  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer と FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> コンテンツを時間でのページで表示モードを表示するには、while<xref:System.Windows.Controls.FlowDocumentScrollViewer>コンテンツを連続したスクロール モードで表示します。  両方<xref:System.Windows.Controls.FlowDocumentPageViewer>と<xref:System.Windows.Controls.FlowDocumentScrollViewer>は特定の表示モードに固定されます。 比較する<xref:System.Windows.Controls.FlowDocumentReader>、さまざまな表示モードを動的に選択するユーザーを有効にする機能が含まれています (によって提供される、<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>列挙型) より多くのリソースよりも処理を要するができますが<xref:System.Windows.Controls.FlowDocumentPageViewer>または<xref:System.Windows.Controls.FlowDocumentScrollViewer>します。  
  
 既定では、垂直スクロール バーは常に表示され、水平スクロール バーは必要に応じて表示されます。 既定の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の<xref:System.Windows.Controls.FlowDocumentScrollViewer>ツールバーには含まれません。 ただし、、<xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A>組み込みツールバーを有効にするプロパティを使用できます。  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>ユーザー インターフェイスのテキスト  
 ドキュメントへのテキストの追加だけでなく、テキストはもちろん、フォームなどのアプリケーション UI で使用できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、画面にテキストを描画するための複数のコントロールが含まれています。 各コントロールは異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。 一般に、<xref:System.Windows.Controls.TextBlock>要素は、制限付きのテキストのサポートがで短い文など、必要な場合に、使用する必要があります、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。 <xref:System.Windows.Controls.Label> 最小限のテキストのサポートが必要な場合に使用できます。 詳細については、「[TextBlock の概要](../controls/textblock-overview.md)」を参照してください。  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>ドキュメントのパッケージ化  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]アプリケーション データ、ドキュメントのコンテンツ、および簡単にアクセスでき、移植性と簡単に配布できますが、単一のコンテナー内の関連リソースを整理する効率的な手段を提供します。 ZIP ファイルの例に示します、<xref:System.IO.Packaging.Package>できる 1 つの単位として複数のオブジェクトを保持する型。 パッケージ[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]既定<xref:System.IO.Packaging.ZipPackage>Open Packaging Conventions 標準を使用して、XML および ZIP ファイル アーキテクチャと設計の実装。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のパッケージ化 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] は、パッケージの作成、およびパッケージへのオブジェクトの格納とそれらのオブジェクトへのアクセスを簡単にします。 格納されているオブジェクト、<xref:System.IO.Packaging.Package>と呼ばれますが、 <xref:System.IO.Packaging.PackagePart> (「パーツ」)。 パッケージには、パーツの発行元を識別し、パッケージのコンテンツが変更されていないことを検証するのに使用できる署名されたデジタル証明書を含めることもできます。  パッケージを含めることも、<xref:System.IO.Packaging.PackageRelationship>をパッケージに追加または既存のパーツのコンテンツを実際に変更することがなく、特定の部分に関連付けられている追加の情報をできるようにする機能。  パッケージ サービスでは、[!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)] もサポートされます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パッケージ アーキテクチャは、さまざまな重要な技術の基盤として機能します。  
  
- [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] に準拠する [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ドキュメント。  
  
- Microsoft Office "12" Open XML 形式のドキュメント (.docx)。  
  
- 独自のアプリケーション設計のカスタム保存形式。  
  
 パッケージ化 Api に基づいて、<xref:System.Windows.Xps.Packaging.XpsDocument>を格納するために設計されて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]固定コンテンツ ドキュメント。 <xref:System.Windows.Xps.Packaging.XpsDocument>自己完結型のドキュメントに表示される、ビューアーで開くことができるは、 <xref:System.Windows.Controls.DocumentViewer> 、印刷スプールにルーティングまたはに直接出力の制御、 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-互換性のあるプリンターです。  
  
 次のセクションでは、追加情報を提供する、<xref:System.IO.Packaging.Package>と<xref:System.Windows.Xps.Packaging.XpsDocument>[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]付属[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
<a name="packages"></a>   
### <a name="package-components"></a>パッケージ コンポーネント  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パッケージ化 API は、アプリケーション データとドキュメントを 1 つの移植可能な単位に編成できるようにします。 ZIP ファイルは、最もよく使用されるパッケージの種類の 1 つであり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で用意されている既定のパッケージの種類です。  <xref:System.IO.Packaging.Package> 元の抽象クラス自体は<xref:System.IO.Packaging.ZipPackage>オープン標準 XML および ZIP ファイル アーキテクチャを使用して実装されます。  <xref:System.IO.Packaging.Package.Open%2A>メソッドは<xref:System.IO.Packaging.ZipPackage>を作成し、既定では、ZIP ファイルを使用します。 パッケージには、次の 3 種類の基本的な項目を含めることができます。  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|アプリケーション コンテンツ、データ、ドキュメント、およびリソース ファイル。|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|識別、認証、および検証のための [X.509 証明書]。|  
|<xref:System.IO.Packaging.PackageRelationship>|パッケージまたは特定のパーツに関連する追加された情報。|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> (「パーツ」) は抽象クラスに格納されているオブジェクトを参照する、<xref:System.IO.Packaging.Package>します。 ZIP ファイルでは、パッケージ パーツは ZIP ファイル内に格納された個別のファイルに対応します。  <xref:System.IO.Packaging.ZipPackagePart> 格納されているシリアル化可能なオブジェクトの既定の実装を提供する<xref:System.IO.Packaging.ZipPackage>します。  ファイル システムと同様に、パッケージに含まれているパーツは、階層的ディレクトリまたは "フォルダー スタイル" 編成で格納されます。  使用して、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Api をパッケージ化、アプリケーション、保存、読み書きできる複数<xref:System.IO.Packaging.PackagePart>オブジェクトを 1 つの ZIP ファイル コンテナーを使用します。  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 セキュリティのため、 <xref:System.IO.Packaging.PackageDigitalSignature> (「デジタル署名」) は、パッケージ内のパーツと関連付けることができます。 A<xref:System.IO.Packaging.PackageDigitalSignature>する [509] が組み込まれています。 2 つの機能を提供します。  
  
1. パーツの発行元を識別および認証します。  
  
2. パーツが変更されていないことを検証します。  
  
 デジタル署名はパーツを変更できなくするものではありませんが、パーツが何らかの方法で変更されている場合、デジタル署名に対する検証チェックは失敗します。 その後、アプリケーションでは適切なアクションを実行することができます。たとえば、パーツを開く操作をブロックしたり、パーツが変更されていて安全ではないことをユーザーに知らせたりすることができます。  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> (「リレーションシップ」) は、パッケージまたはパッケージ内のパーツと追加情報を関連付けるためのメカニズムを提供します。 リレーションシップは、実際のパーツのコンテンツを変更することなく追加情報をパーツに関連付けることができるパッケージ レベルの機能です。 パーツのコンテンツに新しいデータを直接挿入するのは、次のように多くの場合において実用的ではありません。  
  
- パーツの実際の種類およびそのコンテンツ スキーマが不明な場合。  
  
- わかっている場合でも、コンテンツ スキーマが新しい情報を追加する方法を提供しない可能性がある場合。  
  
- パーツが、デジタル署名されたり、暗号化されたり、変更できなくされたりする可能性がある場合。  
  
 パッケージ リレーションシップは、追加情報を個別のパーツまたはパッケージ全体に追加または関連付けるための検出可能な方法を提供します。 パッケージ リレーションシップは、次の 2 つの主要な機能のために使用されます。  
  
1. 1 つのパーツから別のパーツへの依存関係の定義。  
  
2. メモまたはパーツに関連したその他のデータを追加する情報リレーションシップの定義。  
  
 A<xref:System.IO.Packaging.PackageRelationship>依存関係を定義し、パッケージまたはパッケージ全体の一部に関連付けられているその他の情報を追加する迅速で探索可能な手段を提供します。  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>依存関係  
 依存関係は、1 つのパーツによって他のパーツに対して作成される依存関係を記述するために使用されます。 たとえば、パッケージには、1 つ以上の \<img> イメージ タグを含む HTML パーツが含まれている場合があります。 イメージ タグは、パッケージの内部またはパッケージの外部 (インターネット経由でアクセスできる場合など) にあるその他のパーツとして配置されているイメージを参照します。 作成、 <xref:System.IO.Packaging.PackageRelationship> HTML ファイルで検出し、迅速かつ簡単に依存するリソースへのアクセスに関連付けられています。 ブラウザーまたはビューアー アプリケーションは、パーツ リレーションシップに直接アクセスし、スキーマが不明である場合や、ドキュメントの解析を行わない状態でも依存リソースをすぐにアセンブルできます。  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>情報リレーションシップ  
 メモまたは注釈と同様に、<xref:System.IO.Packaging.PackageRelationship>を他の種類のパーツのコンテンツ自体を実際に変更することがなく、パーツに関連する情報を格納できます。  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS ドキュメント  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] ドキュメントは、レンダリングのために必要なすべてのリソースおよび情報と共に 1 つ以上の固定ドキュメントを格納するパッケージです。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] はネイティブな [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 印刷スプール ファイル形式でもあります。  <xref:System.Windows.Xps.Packaging.XpsDocument>は、標準 ZIP データセットに格納され、XML とイメージ、フォント ファイルなどのバイナリ コンポーネントの組み合わせを含めることができます。 [PackageRelationships](#PackageRelationships) は、ドキュメントを完全にレンダリングするために必要なコンテンツとリソースの間の依存関係を定義するために使用されます。  <xref:System.Windows.Xps.Packaging.XpsDocument>デザインが複数の使用をサポートする信頼性の高い 1 つのドキュメント ソリューションを提供します。  
  
- 単一の移植可能で配布しやすいファイルとして、固定ドキュメント コンテンツおよびリソースを読み取り、書き込み、および格納する。  
  
- [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ビューアー アプリケーションを使用してドキュメントを表示する。  
  
- [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] のネイティブな印刷スプール出力形式でドキュメントを出力する。  
  
- [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] と互換性があるプリンターにドキュメントを直接ルーティングする。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Text](optimizing-performance-text.md)
- [フロー ドキュメントの概要](flow-document-overview.md)
- [印刷の概要](printing-overview.md)
- [ドキュメントのシリアル化および保存](document-serialization-and-storage.md)

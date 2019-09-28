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
ms.openlocfilehash: e21abca4dd02a849d0240888f831125ab96aa8f1
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393279"
---
# <a name="documents-in-wpf"></a>WPF のドキュメント
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、以前の世代の Windows よりも簡単にアクセスして読み取ることができるように設計された忠実度の高いコンテンツを作成できるようにする幅広いドキュメント機能が用意されています。 拡張された機能と品質に加えて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ドキュメントの表示、パッケージ化、およびセキュリティの統合されたサービスも提供します。 ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のドキュメントの種類とドキュメントのパッケージ化の概要を説明します。  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>ドキュメントの種類  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ドキュメントは用途に基づいて大きく 2 つのカテゴリに分けられます。これらのドキュメントのカテゴリは "固定ドキュメント" および "フロー ドキュメント" と呼ばれます。  
  
 固定ドキュメントは、使用されるディスプレイまたはプリンター ハードウェアに関係なく、正確な [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] プレゼンテーションを必要とするアプリケーションを対象に用意されています。 固定ドキュメントの一般的な用途としては、元のページ デザインに準拠していることが重要になるデスクトップ パブリッシング、ワード プロセッシング、およびフォーム レイアウトなどがあります。 レイアウトの一部として、固定ドキュメントでは、使用中のディスプレイまたは印刷デバイスに依存しないコンテンツ要素の正確な配置位置が保持されます。 たとえば、96 dpi のディスプレイに表示される固定ドキュメント ページは、600 dpi のレーザー プリンターに出力される場合に、4800 dpi の写真植字に出力される場合とまったく同じように表示されます。 ドキュメントの品質は各デバイスの機能に応じて最大化されますが、ページ レイアウトはすべての場合において同じになります。  
  
 これに対して、フロー ドキュメントは、表示と読みやすさを最適化するように設計されており、ドキュメントが主に読みやすさを目的としている場合に最適です。 フロー ドキュメントは、1 つの定義済みのレイアウトに設定するのではなく、ウィンドウのサイズ、デバイスの解像度、省略可能なユーザー設定など、ランタイム変数に基づいてコンテンツを動的に調整したりリフローしたりします。 Web ページは、そのコンテンツが現在のウィンドウに収まるように動的にフォーマットされるフロー ドキュメントの簡単な例です。 フロー ドキュメントは、ランタイム環境に基づいて、ユーザーにとっての表示と読みやすさを最適化します。 たとえば、同じフロー ドキュメントでも、高解像度の 19 インチ ディスプレイなのか、小型の 2x3 インチの PDA 画面なのかに応じて、最も読みやすくなるように書式設定が動的に変更されます。 また、フロー ドキュメントには、検索、読みやすさを最適化するモードの表示、およびフォントのサイズと外観を変更する機能を含むさまざまな組み込み機能があります。  フロー ドキュメントの図、例、および詳細については、「[フロー ドキュメントの概要](flow-document-overview.md)」を参照してください。  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>ドキュメント コントロールとテキスト レイアウト  
 .NET Framework には、アプリケーション内の固定ドキュメント、フロードキュメント、および一般的なテキストを簡単に使用できるように構築された一連のコントロールが用意されています。  固定ドキュメントコンテンツの表示は、@no__t 0 コントロールを使用してサポートされます。  フロードキュメントの内容の表示は、3つの異なるコントロール (@no__t 0、<xref:System.Windows.Controls.FlowDocumentPageViewer>、<xref:System.Windows.Controls.FlowDocumentScrollViewer>) によってサポートされています。これは、さまざまなユーザーシナリオにマップします (以下のセクションを参照してください)。  その他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールでは、一般的なテキストの使用をサポートする簡略化されたレイアウトが提供されます (後述の「[ユーザー インターフェイスのテキスト](#text_in_the_user_interface)」を参照してください)。  
  
### <a name="fixed-document-control---documentviewer"></a>固定ドキュメント コントロール - DocumentViewer  
 @No__t 0 コントロールは、<xref:System.Windows.Documents.FixedDocument> のコンテンツを表示するように設計されています。 @No__t 0 コントロールは、印刷出力、クリップボードへのコピー、ズーム、テキスト検索機能など、一般的な操作の組み込みサポートを提供する直感的なユーザーインターフェイスを提供します。 コントロールは、使い慣れたスクロール機構を使用してコンテンツのページへのアクセスを提供します。 すべての @no__t のコントロールと同様に、@no__t は完全または部分的なスタイル設定をサポートしています。これにより、コントロールを事実上あらゆるアプリケーションや環境に視覚的に統合できます。  
  
 <xref:System.Windows.Controls.DocumentViewer> は、読み取り専用の方法でコンテンツを表示するように設計されています。コンテンツの編集または変更は使用できず、サポートされていません。  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>フロー ドキュメント コントロール  

> [!NOTE]
> フロードキュメントの機能とその作成方法の詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください。  
  
 フロードキュメントの内容の表示は、3つのコントロール (<xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer>、<xref:System.Windows.Controls.FlowDocumentScrollViewer>) でサポートされています。  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>には、ユーザーがさまざまな表示モードを動的に選択できるようにする機能が用意されています。これには、シングルページ (一度に1ページ) 表示モード、2ページずつ (書籍読み取り形式) 表示モード、および連続スクロール (制限カラム) 表示モードが含まれます。  これらの表示モードの詳細について<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>は、「」を参照してください。  さまざまな表示<xref:System.Windows.Controls.FlowDocumentPageViewer>モードを動的に切り替える機能が不要な場合は、特定<xref:System.Windows.Controls.FlowDocumentScrollViewer>の表示モードで固定されている軽量のフローコンテンツビューアーを提供します。  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer と FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>コンテンツを同時に表示モードで表示します。一方<xref:System.Windows.Controls.FlowDocumentScrollViewer> 、連続スクロールモードでコンテンツを表示します。  と<xref:System.Windows.Controls.FlowDocumentPageViewer>は<xref:System.Windows.Controls.FlowDocumentScrollViewer>どちらも、特定の表示モードに固定されています。 と比較します。これには<xref:System.Windows.Controls.FlowDocumentReaderViewingMode> <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> <xref:System.Windows.Controls.FlowDocumentReader>、ユーザーがさまざまな表示モード (列挙体によって提供される) を動的に選択できるようにする機能が含まれています。これにより、またはより多くのリソースが消費されます。  
  
 既定では、垂直スクロール バーは常に表示され、水平スクロール バーは必要に応じて表示されます。 @No__t-1 の既定の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] には、ツールバーは含まれません。ただし、<xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> プロパティを使用して、組み込みのツールバーを有効にすることができます。  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>ユーザー インターフェイスのテキスト  
 ドキュメントへのテキストの追加だけでなく、テキストはもちろん、フォームなどのアプリケーション UI で使用できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、画面にテキストを描画するための複数のコントロールが含まれています。 各コントロールは異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。 一般に、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の簡単な文など、制限されたテキストのサポートが必要な場合は、<xref:System.Windows.Controls.TextBlock> 要素を使用する必要があります。 <xref:System.Windows.Controls.Label> は、最小限のテキストのサポートが必要な場合に使用できます。 詳細については、「[TextBlock の概要](../controls/textblock-overview.md)」を参照してください。  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>ドキュメントのパッケージ化  
 @No__t 0 Api は、アプリケーションデータ、ドキュメントコンテンツ、および関連リソースを、簡単にアクセス、移植、および配布しやすい1つのコンテナーに整理するための効率的な手段を提供します。 ZIP ファイルは、複数のオブジェクトを1つの単位として保持できる @no__t 0 型の例です。 パッケージ化 Api には、XML および ZIP ファイルアーキテクチャを含むオープンパッケージング規則標準を使用して設計された既定の <xref:System.IO.Packaging.ZipPackage> 実装が用意されています。 @No__t 0 のパッケージ化 Api を使用すると、パッケージを簡単に作成し、その中にオブジェクトを格納してアクセスすることができます。 @No__t 0 に格納されているオブジェクトは、<xref:System.IO.Packaging.PackagePart> ("part") と呼ばれます。 パッケージには、パーツの発行元を識別し、パッケージのコンテンツが変更されていないことを検証するのに使用できる署名されたデジタル証明書を含めることもできます。  パッケージには、パッケージに追加情報を追加したり、既存のパーツの内容を実際に変更することなく特定の部分に関連付けたりするための @no__t 0 機能も含まれています。  パッケージサービスでは、Microsoft Windows Rights Management (RM) もサポートしています。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パッケージ アーキテクチャは、さまざまな重要な技術の基盤として機能します。  
  
- XML Paper Specification (XPS) に準拠する XPS ドキュメント。  
  
- Microsoft Office "12" Open XML 形式のドキュメント (.docx)。  
  
- 独自のアプリケーション設計のカスタム保存形式。  
  
 パッケージ化 Api に基づいて、@no__t 0 は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の固定コンテンツドキュメントを格納するために特別に設計されています。 @No__t 0 は自己完結型のドキュメントであり、ビューアーで開く、@no__t 1 のコントロールに表示する、印刷スプールにルーティングする、XPS 互換プリンターに直接出力する、のいずれかになります。  
  
 以下のセクションでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で提供される <xref:System.IO.Packaging.Package> および <xref:System.Windows.Xps.Packaging.XpsDocument> Api に関する追加情報を提供します。  
  
<a name="packages"></a>   
### <a name="package-components"></a>パッケージ コンポーネント  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パッケージ化 API は、アプリケーション データとドキュメントを 1 つの移植可能な単位に編成できるようにします。 ZIP ファイルは、最もよく使用されるパッケージの種類の 1 つであり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で用意されている既定のパッケージの種類です。  <xref:System.IO.Packaging.Package> 自体は、オープンな標準 XML および ZIP ファイルアーキテクチャを使用して <xref:System.IO.Packaging.ZipPackage> が実装される抽象クラスです。  @No__t-0 メソッドでは、既定で ZIP ファイルを作成して使用するために <xref:System.IO.Packaging.ZipPackage> を使用します。 パッケージには、次の 3 種類の基本的な項目を含めることができます。  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|アプリケーション コンテンツ、データ、ドキュメント、およびリソース ファイル。|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|識別、認証、および検証のための [X.509 証明書]。|  
|<xref:System.IO.Packaging.PackageRelationship>|パッケージまたは特定のパーツに関連する追加された情報。|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 @No__t-0 ("part") は、<xref:System.IO.Packaging.Package> に格納されているオブジェクトを参照する抽象クラスです。 ZIP ファイルでは、パッケージ パーツは ZIP ファイル内に格納された個別のファイルに対応します。  <xref:System.IO.Packaging.ZipPackagePart> @no__t に格納されているシリアル化可能なオブジェクトの既定の実装を提供します。  ファイル システムと同様に、パッケージに含まれているパーツは、階層的ディレクトリまたは "フォルダー スタイル" 編成で格納されます。  アプリケーションでは、@no__t 0 のパッケージ Api を使用して、1つの ZIP ファイルコンテナーを使用して複数の @no__t オブジェクトの書き込み、格納、および読み取りを行うことができます。  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 セキュリティのために、パッケージ内のパーツには @no__t 0 ("デジタル署名") を関連付けることができます。 @No__t-0 には、次の2つの機能を提供する [509] が組み込まれています。  
  
1. パーツの発行元を識別および認証します。  
  
2. パーツが変更されていないことを検証します。  
  
 デジタル署名はパーツを変更できなくするものではありませんが、パーツが何らかの方法で変更されている場合、デジタル署名に対する検証チェックは失敗します。 その後、アプリケーションでは適切なアクションを実行することができます。たとえば、パーツを開く操作をブロックしたり、パーツが変更されていて安全ではないことをユーザーに知らせたりすることができます。  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 @No__t-0 ("relationship") は、パッケージまたはパッケージ内のパーツに追加情報を関連付けるためのメカニズムを提供します。 リレーションシップは、実際のパーツのコンテンツを変更することなく追加情報をパーツに関連付けることができるパッケージ レベルの機能です。 パーツのコンテンツに新しいデータを直接挿入するのは、次のように多くの場合において実用的ではありません。  
  
- パーツの実際の種類およびそのコンテンツ スキーマが不明な場合。  
  
- わかっている場合でも、コンテンツ スキーマが新しい情報を追加する方法を提供しない可能性がある場合。  
  
- パーツが、デジタル署名されたり、暗号化されたり、変更できなくされたりする可能性がある場合。  
  
 パッケージ リレーションシップは、追加情報を個別のパーツまたはパッケージ全体に追加または関連付けるための検出可能な方法を提供します。 パッケージ リレーションシップは、次の 2 つの主要な機能のために使用されます。  
  
1. 1 つのパーツから別のパーツへの依存関係の定義。  
  
2. メモまたはパーツに関連したその他のデータを追加する情報リレーションシップの定義。  
  
 @No__t-0 は、依存関係を定義し、パッケージまたはパッケージ全体に関連付けられたその他の情報を追加するための、迅速で発見可能な手段を提供します。  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>依存関係  
 依存関係は、1 つのパーツによって他のパーツに対して作成される依存関係を記述するために使用されます。 たとえば、パッケージには、1 つ以上の \<img> イメージ タグを含む HTML パーツが含まれている場合があります。 イメージ タグは、パッケージの内部またはパッケージの外部 (インターネット経由でアクセスできる場合など) にあるその他のパーツとして配置されているイメージを参照します。 HTML ファイルに関連付けられている @no__t 0 を作成すると、依存リソースをすばやく簡単に検出してアクセスできます。 ブラウザーまたはビューアー アプリケーションは、パーツ リレーションシップに直接アクセスし、スキーマが不明である場合や、ドキュメントの解析を行わない状態でも依存リソースをすぐにアセンブルできます。  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>情報リレーションシップ  
 メモや注釈と同様に、@no__t 0 を使用して、パートコンテンツ自体を実際に変更することなく、パートに関連付けられている他の種類の情報を格納することもできます。  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS ドキュメント  
 XML Paper Specification (XPS) ドキュメントは、レンダリングに必要なすべてのリソースと情報と共に1つ以上の固定ドキュメントを含むパッケージです。  XPS は、ネイティブ [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] の印刷スプールファイル形式でもあります。  @No__t 0 は標準の ZIP データセットに格納され、XML およびバイナリコンポーネント (イメージやフォントファイルなど) の組み合わせを含めることができます。 [PackageRelationships](#PackageRelationships) は、ドキュメントを完全にレンダリングするために必要なコンテンツとリソースの間の依存関係を定義するために使用されます。  @No__t 0 の設計では、複数の使用をサポートする、忠実度の高い単一のドキュメントソリューションを提供します。  
  
- 単一の移植可能で配布しやすいファイルとして、固定ドキュメント コンテンツおよびリソースを読み取り、書き込み、および格納する。  
  
- XPS ビューアーアプリケーションを使用してドキュメントを表示する。  
  
- [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] のネイティブな印刷スプール出力形式でドキュメントを出力する。  
  
- XPS 互換プリンターにドキュメントを直接ルーティングする。  
  
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

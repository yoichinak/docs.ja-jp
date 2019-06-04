---
title: XAML サービス
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 61b141642fa3745c3abcf8d0234f70373fa5485e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491110"
---
# <a name="xaml-services"></a>XAML サービス
このトピックでは、サービスの .NET Framework XAML と呼ばれるテクノロジ一連の機能について説明します。 サービスと記述された Api の大半は、.NET core アセンブリの一連の .NET Framework 4 で導入されたアセンブリである、System.Xaml アセンブリに配置されます。 サービスには、リーダーとライターは、スキーマのクラスおよびスキーマのサポート、ファクトリ クラス、XAML 言語の組み込みサポート、およびその他の XAML 言語機能の属性を設定します。  
  
## <a name="about-this-documentation"></a>このドキュメントについて  
 .NET Framework XAML サービスの概念に関するドキュメントでは、XAML 言語とその可能性がありますに適用する方法、特定のフレームワークなどの経験があると想定[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Workflow Foundation、または特定のテクノロジの機能領域で、たとえば、ビルドのカスタマイズ機能<xref:Microsoft.Build.Framework.XamlTypes>します。 このドキュメントは、マークアップ言語、XAML 構文の用語、またはその他の入門資料として XAML の基本を説明しません。 代わりに、このドキュメントは、具体的には、System.Xaml アセンブリ ライブラリで有効になっている .NET Framework XAML サービスの使用に焦点を当てています。 これらの Api のほとんどは、XAML 言語の統合と拡張のシナリオです。 次のいずれかがあります。  
  
- 基本の XAML リーダーまたは XAML ライター (XAML ノード ストリームを直接処理は、独自の XAML リーダーまたは XAML ライターの派生) の機能を拡張します。  
  
- 特定のフレームワークの依存関係がない XAML 使用可能なカスタム型を定義して、XAML を伝達するために、型の属性を設定する .NET Framework XAML サービスのシステム特性を入力します。  
  
- ビジュアル デザイナーまたは対話型エディターの XAML マークアップ ソースなどのアプリケーションのコンポーネントとして、XAML リーダーまたは XAML ライターをホストします。  
  
- XAML 値コンバーター (マークアップ拡張機能はカスタム型の型コンバーター) を記述します。  
  
- カスタム XAML スキーマ コンテキストを定義する (バッキング型のソースを別のアセンブリ読み込みの手法を使用して、アセンブリの反映; CLR を使用して読み込まれたアセンブリの概念を使用して既知の型参照の手法を使用して、常にではなく;`AppDomain`とその関連付けられているセキュリティ モデル)。  
  
- 基本の XAML 型システムを拡張します。  
  
- 使用して、`Lookup`または`Invoker`XAML に影響するための手法は、システムと型 backings を評価する方法を入力します。  
  
 言語として XAML の入門資料を探している場合[XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)します。 そのトピックについて説明します XAML 新たに導入された対象ユーザーの両方を[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]と XAML マークアップと XAML 言語機能を使用することもできます。 別の便利なドキュメントがの入門資料、 [XAML 言語仕様](https://go.microsoft.com/fwlink/?LinkId=114525)します。  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML サービスと .NET アーキテクチャでは System.Xaml  
 Microsoft .NET Framework の以前のバージョン、XAML 言語機能が実装される、Microsoft .NET Framework 上に構築されたフレームワークのためのサポート ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、Windows Workflow Foundation と Windows Communication Foundation (WCF))、そのため、その動作と API を使用する特定のフレームワークに応じて使用していたが変化します。 これは、中には、XAML パーサーと、オブジェクト グラフの作成メカニズム、XAML 言語の組み込み、シリアル化のサポート、およびなど。  
  
 .NET Framework 4、.NET Framework XAML サービスおよび System.Xaml アセンブリでは、XAML 言語機能をサポートするために必要なものの多くを定義します。 これには、XAML リーダーと XAML ライターの基本クラスが含まれます。 フレームワーク固有の XAML 実装のいずれかでなかった、.NET Framework XAML サービスに追加された最も重要な機能は、XAML の型システム表現です。 型システム表現は、特定の機能のフレームワークに依存することがなく XAML の機能を中心にオブジェクト指向の方法で XAML を表示します。  
  
 XAML 型システムは、マークアップ形式または XAML の生成元の実行時の詳細によっては制限されません。任意の特定のバッキング型システムによってに制限されます。 XAML 型システムには、型、メンバー、XAML スキーマ コンテキスト、XML レベルの概念、およびその他の XAML 言語の概念または XAML の組み込みのオブジェクト表現が含まれています。 使用して、または XAML 型システムの拡張により、XAML リーダーと XAML ライターのようなクラスから派生し、フレームワーク、テクノロジ、または使用するアプリケーションを有効になっている特定の機能に XAML 表現の機能を拡張すること、またはXAML を生成します。 XAML スキーマ コンテキストの概念により、XAML オブジェクト ライター実装、テクノロジのバッキング型システム、コンテキストと XAML ノード内のアセンブリ情報を通じて伝達との組み合わせから実用的なオブジェクト グラフの書き込み操作ソース。 XAML スキーマの概念の詳細についてはします。 参照してください[既定の XAML スキーマ コンテキストと WPF XAML スキーマ コンテキスト](default-xaml-schema-context-and-wpf-xaml-schema-context.md)します。  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML ノード ストリーム、XAML リーダーおよび XAML ライター  
 .NET Framework XAML サービスは、XAML 言語と言語として XAML を使用して、特定のテクノロジ間のリレーションシップで果たしている役割を理解するのには、XAML ノード ストリームとその概念による API の図形の概念を理解して用語集。 XAML ノード ストリームは、XAML 言語の表現と、XAML を表すかを定義するオブジェクト グラフ間の中間概念です。  
  
- XAML リーダーは、何らかの形式で XAML を処理し、XAML ノード ストリームを生成するエンティティです。 API では、XAML リーダーは、基本クラスによって表される<xref:System.Xaml.XamlReader>します。  
  
- XAML ライターは、XAML ノード ストリームを処理し、別のものを生成するエンティティです。 API では、XAML ライターが、基本クラスによって表される<xref:System.Xaml.XamlWriter>します。  
  
 XAML に関連する 2 つの最も一般的なシナリオのオブジェクト グラフをインスタンス化する XAML を読み込み、アプリケーションやツールからのオブジェクト グラフの保存と (通常はマークアップ形式をテキスト ファイルとして保存) での XAML 表現を生成していること。 XAML の読み込みと、オブジェクト グラフの作成は、読み込みパスとしては、このドキュメントで多くの場合、呼ばれます。 保存または既存のオブジェクト グラフを XAML にシリアル化する多くの場合で参照されて保存先として、このドキュメントのパス。  
  
 読み込みパスの最も一般的な種類は、次のように記述できます。  
  
- UTF エンコードされた XML 形式での XAML 表現を起動し、テキスト ファイルとして保存します。  
  
- その XAML を読み込む<xref:System.Xaml.XamlXmlReader>します。 <xref:System.Xaml.XamlXmlReader> <xref:System.Xaml.XamlReader>サブクラスです。  
  
- 結果は、XAML ノード ストリームです。 使用して XAML ノード ストリームの個々 のノードにアクセスできる<xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API。 最も一般的な操作をここでは、XAML ノード ストリームの「現在のレコード」を使用して各ノードの処理に進むにはメタファです。  
  
- XAML ノード ストリームからの結果として得られるノードを渡す、 <xref:System.Xaml.XamlObjectWriter> API。 <xref:System.Xaml.XamlObjectWriter> <xref:System.Xaml.XamlWriter>サブクラスです。  
  
- <xref:System.Xaml.XamlObjectWriter>ソース XAML ノード ストリームを使用して進行状況に従って、一度に 1 つのオブジェクト、オブジェクト グラフを書き込みます。 これは、XAML スキーマ コンテキストと、アセンブリと、バッキング型システムとフレームワークの型にアクセスできる実装の支援を行います。  
  
- 呼び出す<xref:System.Xaml.XamlObjectWriter.Result%2A>オブジェクト グラフのルート オブジェクトを取得する XAML ノード ストリームの末尾にします。  
  
 保存パスの最も一般的な種類は、次のように記述できます。  
  
- 実行全体のアプリケーション時間を UI のコンテンツおよび実行時にアプリケーション全体のオブジェクト表現の小さいセグメント、または、実行時の状態のオブジェクト グラフを起動します。  
  
- アプリケーションのルートやドキュメントのルートなどの論理的開始オブジェクトから読み込むオブジェクトを<xref:System.Xaml.XamlObjectReader>します。 <xref:System.Xaml.XamlObjectReader> <xref:System.Xaml.XamlReader>サブクラスです。  
  
- 結果は、XAML ノード ストリームです。 使用して XAML ノード ストリームの個々 のノードにアクセスできる<xref:System.Xaml.XamlObjectReader>と<xref:System.Xaml.XamlReader>API。 最も一般的な操作をここでは、XAML ノード ストリームの「現在のレコード」を使用して各ノードの処理に進むにはメタファです。  
  
- XAML ノード ストリームからの結果として得られるノードを渡す、 <xref:System.Xaml.XamlXmlWriter> API。 <xref:System.Xaml.XamlXmlWriter> <xref:System.Xaml.XamlWriter>サブクラスです。  
  
- <xref:System.Xaml.XamlXmlWriter>エンコードを XML UTF で XAML を書き込みます。 これは、ストリーム、またはその他の形式でテキスト ファイルとして保存できます。  
  
- 呼び出す<xref:System.Xaml.XamlXmlWriter.Flush%2A>最終的な出力を取得します。  
  
 XAML ノード ストリームの概念の詳細については、「[XAML ノード ストリームの構造と概念について](understanding-xaml-node-stream-structures-and-concepts.md)」を参照してください。  
  
### <a name="the-xamlservices-class"></a>XamlServices クラス  
 常に XAML ノード ストリームを処理するために必要です Api を使用する場合は、基本的な読み込みパスまたは保存パスの基本的な場合は、<xref:System.Xaml.XamlServices>クラス。  
  
- さまざまな署名<xref:System.Xaml.XamlServices.Load%2A>読み込みパスの実装します。 ファイルまたはストリームを読み込むことができますか、または読み込むことができますが、 <xref:System.Xml.XmlReader>、<xref:System.IO.TextReader>または<xref:System.Xaml.XamlReader>そのリーダーの Api で読み込むことによって、XAML 入力をラップします。  
  
- さまざまな署名<xref:System.Xaml.XamlServices.Save%2A>オブジェクト グラフを保存し、ストリームとしての出力はファイル、または<xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter>インスタンス。  
  
- <xref:System.Xaml.XamlServices.Transform%2A> XAML を変換、読み込みパスと保存をリンクすることで 1 回の操作のパス。 別のスキーマ コンテキストまたは異なるバッキング型システムを使用できます<xref:System.Xaml.XamlReader>と<xref:System.Xaml.XamlWriter>、これは、結果の XAML を変換する方法に影響します。  
  
 使用する方法の詳細についての<xref:System.Xaml.XamlServices>を参照してください[XAMLServices クラスおよび基本的な XAML の読み取りまたは書き込み](xamlservices-class-and-basic-xaml-reading-or-writing.md)します。  
  
## <a name="xaml-type-system"></a>XAML 型システム  
 XAML 型システムは、XAML ノード ストリームの特定の個々 のノードを使用するために必要な Api を提供します。  
  
 <xref:System.Xaml.XamlType> 開始オブジェクト ノードと終了オブジェクト ノード間で処理しているとして使用するオブジェクトの表現です。  
  
 <xref:System.Xaml.XamlMember> メンバー ノードの開始と終了メンバー ノード間で処理しているとして使用するオブジェクトのメンバーの表現です。  
  
 などの Api<xref:System.Xaml.XamlType.GetAllMembers%2A>と<xref:System.Xaml.XamlType.GetMember%2A>と<xref:System.Xaml.XamlMember.DeclaringType%2A>間の関係をレポートする<xref:System.Xaml.XamlType>と<xref:System.Xaml.XamlMember>。  
  
 .NET Framework XAML サービスによって実装される XAML 型システムの既定の動作は、リフレクションを使用して、共通言語ランタイム (CLR) とアセンブリの CLR 型の静的分析に基づくです。 そのため、特定の CLR 型 XAML 型システムの既定の実装型とそのメンバーの XAML スキーマを公開でき、XAML 型システムの観点からそれを報告できます。 既定の XAML 型システムでできるかどうかの型の概念は CLR の継承にマップし、インスタンスや値型の概念がサポートする動作や、CLR の機能にもマップされます。  
  
## <a name="reference-for-xaml-language-features"></a>XAML 言語機能のリファレンス  
 XAML をサポートするためには、.NET Framework XAML サービスは、XAML 言語の XAML 名前空間に定義されている XAML 言語の概念の特定の実装を提供します。 これらは、特定の参照ページとして記載されています。 XAML リーダーまたは .NET Framework XAML サービスで定義されている XAML ライターによって処理されるときに、これらの言語機能がどのように動作するかの観点からは、言語機能が記載されています。 詳細については、次を参照してください[XAML Namespace (x:)。言語機能](xaml-namespace-x-language-features.md)します。

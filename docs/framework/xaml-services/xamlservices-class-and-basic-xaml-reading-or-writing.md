---
title: XAMLServices クラスおよび基本的な XAML の読み取りまたは書き込み
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: c9ef6a215587750f66d2cf8b5b54cbc51f89037e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938737"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>XAMLServices クラスおよび基本的な XAML の読み取りまたは書き込み
<xref:System.Xaml.XamlServices> は、XAML ノード ストリーム、またはこれらのノードから取得された XAML 型システム情報への固有のアクセスを必要としない XAML シナリオに対応するために使用できる、.NET Framework XAML サービスによって提供されるクラスです。 要約すると、<xref:System.Xaml.XamlServices> API は次のように説明できます。 `Load` または `Parse` to suppまたはt a XAML load path, `Save` to suppまたはt a XAML save path, and `Transform` で読み込みパスと保存パスを連結する方法を指定します。 `Transform` は、XAML スキーマを別の XAML スキーマに変更するために使用できます。 このトピックでは、それぞれの API 分類について要約し、特定のメソッド オーバーロード間の相違点について説明します。  
  
<a name="load"></a>   
## <a name="load"></a>Load  
 <xref:System.Xaml.XamlServices.Load%2A> のさまざまなオーバーロードは、読み込みパスのロジック全体を実装しています。 読み込みパスは、ある形式の XAML を使用して XAML ノード ストリームを出力します。 これらの読み込みパスのほとんどは、エンコードされた XML テキスト ファイル形式で XAML を使用します。 ただし、一般的なストリームを読み込むことも、異なる <xref:System.Xaml.XamlReader> 実装に既に含まれているプリロード済みの XAML ソースを読み込むこともできます。  
  
 ほとんどのシナリオにおいて最もシンプルなオーバーロードは、 <xref:System.Xaml.XamlServices.Load%28System.String%29>です。 このオーバーロードには、読み込まれる XAML を含むテキスト ファイル名を表す `fileName` パラメーターがあります。 これは、以前にローカル コンピューターに対してシリアル化された状態またはデータを持つ、完全信頼アプリケーションなどのアプリケーション シナリオに適しています。 また、アプリケーション モデル (フレームワーク) を定義している場合に、アプリケーションの動作、開始 UI、またはフレームワークによって定義された XAML を使用するその他の機能を定義した標準ファイルの 1 つを読み込む場合にも便利です。  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> にも、類似したシナリオがあります。 <xref:System.IO.Stream> はファイル システムにアクセスできるその他の <xref:System.IO> API の出力として頻繁に使用されるため、読み込むファイルをユーザーが選択できるようにする場合は、このオーバーロードが便利です。 または、非同期ダウンロードや、ストリームを生成するその他のネットワーク技術を使用して XAML ソースにアクセスすることもできます。 (ストリームまたはユーザーが選択したソースからの読み込みは、セキュリティに影響が出ることがあります。 詳しくは、「 [XAML Security Considerations](xaml-security-considerations.md)」をご覧ください。)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> と <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> は、.NET Framework の前のバージョンの形式のリーダーに依存するオーバーロードです。 これらのオーバーロードを使用するには、あらかじめリーダー インスタンスを作成し、その `Create` API を使用して XAML を関連形式 (テキストまたは XML) に読み込む必要があります。 レコード ポインターを他のリーダーに既に移動したり、またはレコード ポインターを使用して他の操作を実行したりした場合でも、そのことは問題になりません。 <xref:System.Xaml.XamlServices.Load%2A> からの読み込みパス ロジックは、常にルート以下の XAML 入力全体を処理します。 これらのオーバーロードのシナリオには、次のものがあります。  
  
- 既存の XML 用テキスト エディターを利用してシンプルな XAML 編集機能を提供するデザイン サーフェイス。  
  
- 専用のリーダーを使用してファイルまたはストリームを開く、コア <xref:System.IO> の派生シナリオ。 XAML として読み込む前に、コンテンツの基本的なチェックや処理をロジックで実行します。  
  
 ファイルまたはストリームを読み込むか、XAML 入力をラップした <xref:System.Xml.XmlReader>、 <xref:System.IO.TextReader>、または <xref:System.Xaml.XamlReader> を (そのリーダーの API を使用して読み込むことにより) 読み込むことができます。  
  
 内部的には、上に示した各オーバーロードは最終的に <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>になり、渡された <xref:System.Xml.XmlReader> は新しい <xref:System.Xaml.XamlXmlReader>を作成するために使用されます。  
  
 より高度なシナリオを提供する `Load` シグネチャは <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>です。 このシグネチャは、次のいずれかのケースで使用できます。  
  
- <xref:System.Xaml.XamlReader>の独自の実装を定義した場合。  
  
- 既定の設定とは異なる設定を <xref:System.Xaml.XamlReader> に指定する必要がある場合。  
  
 既定以外の設定は、たとえば次のものに対する設定です: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>、 <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>、 <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>、 <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>、 <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>。 <xref:System.Xaml.XamlServices> の既定のリーダーは <xref:System.Xaml.XamlXmlReader>です。 独自の <xref:System.Xaml.XamlXmlReader>を提供する場合の設定では、次のプロパティが既定値以外に設定されます: <xref:System.Xaml.XamlXmlReaderSettings>、 <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>、 <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>、 <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>、 <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>。  
  
<a name="parse"></a>   
## <a name="parse"></a>Parse  
 <xref:System.Xaml.XamlServices.Parse%2A> は、XAML 入力から XAML ノード ストリームを作成する読み込みパス API であるため、 `Load` に似ています。 ただし、この場合の XAML 入力は、読み込まれる XAML 全体を含む文字列として直接指定されます。 <xref:System.Xaml.XamlServices.Parse%2A> は軽量のアプローチであり、フレームワーク シナリオよりもアプリケーション シナリオにより適しています 詳細については、「 <xref:System.Xaml.XamlServices.Parse%2A>」を参照してください。 実際には、<xref:System.Xaml.XamlServices.Parse%2A> はラップされた <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> 呼び出しで、内部では <xref:System.IO.StringReader> を使用します。  
  
<a name="save"></a>   
## <a name="save"></a>Save  
 <xref:System.Xaml.XamlServices.Save%2A> のさまざまなオーバーロードは、保存パスを実装しています。 どの <xref:System.Xaml.XamlServices.Save%2A> メソッドもオブジェクト グラフを入力として取り、ストリーム、ファイル、または <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> インスタンスとして出力を生成します。  
  
 入力オブジェクトは、何らかのオブジェクト表現のルート オブジェクトであると想定されます。 ビジネス オブジェクトの単一ルート、UI シナリオでのページのオブジェクト ツリーのルート、デザイン ツールの作業用の編集サーフェイス、またはシナリオに適したその他のルート オブジェクト概念などが考えられます。  
  
 多くのシナリオでは、保存されるオブジェクト ツリーは、 <xref:System.Xaml.XamlServices.Load%2A> またはフレームワーク/アプリケーション モデルによって実装されたその他の API で XAML をロードした元の操作に関連しています。 状態の変更、アプリケーションがユーザーからキャプチャしたランタイム設定の変更、アプリケーションが XAML デザイン サーフェイスであるために発生する XAML の変更などにより、キャプチャされるオブジェクト ツリーに相違が生じることもあります。変更の有無にかかわらず、まずマークアップから XAML を読み込んで再保存し、2 つの XAML マークアップ フォームを比較するという概念は、XAML のラウンド トリップ表現と呼ばれることがあります。  
  
 マークアップ形式で設定された複合オブジェクトの保存とシリアル化に伴う課題は、完全な表現によって情報を失われないようにすることと、XAML が詳細すぎてユーザーが判読しにくい状態になることとの間のバランスを取ることです。 さらに、XAML を使用する顧客が異なれば、このバランスをどのように取るかの定義や要求も異なることがあります <xref:System.Xaml.XamlServices.Save%2A> API は、このバランスの定義の 1 つを表します。 <xref:System.Xaml.XamlServices.Save%2A> は、使用できる XAML スキーマ コンテキストと、 <xref:System.Xaml.XamlType>、 <xref:System.Xaml.XamlMember>の既定の CLR ベースの特性、およびその他の組み込み XAML と XAML 型システムの概念を使用し、ある XAML ノード ストリーム構造をマークアップに再保存するときに、どこで最適化するかを決定します。 たとえば、 <xref:System.Xaml.XamlServices> の保存パスでは、CLR ベースの既定の XAML スキーマ コンテキストを使用してオブジェクトの <xref:System.Xaml.XamlType> を解決し、 <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>を決定したうえで、このオブジェクトの XAML コンテンツにプロパティを記述するときにプロパティ要素タグを省略できます。  
  
<a name="transform"></a>   
## <a name="transform"></a>変換  
 <xref:System.Xaml.XamlServices.Transform%2A> は、読み込みパスと保存パスを単一の操作としてリンクすることによって、XAML を変換します。 <xref:System.Xaml.XamlReader> および <xref:System.Xaml.XamlWriter>に対して異なるスキーマ コンテキストまたは異なるバッキング型システムを使用できます。これは、結果として生成される XAML がどのように変換されるかに影響します。 これは、さまざまな変換操作で機能します。  
  
 XAML ノード ストリームの各ノードの確認に依存する操作については、通常、 <xref:System.Xaml.XamlServices.Transform%2A>は使用しません。 代わりに、読み込みパスから保存パスへの一連の操作を独自に定義し、独自のロジックを挿入する必要があります。 たとえば、独自のノード ループの中で XAML リーダーと XAML ライターのペアを使用します。 具体的に言うと、 <xref:System.Xaml.XamlXmlReader> を使用して最初の XAML を読み込み、 <xref:System.Xaml.XamlXmlReader.Read%2A> を連続的に呼び出してノードにステップ インします。 XAML ノード ストリーム レベルの操作では、個々のノード (型、メンバー、その他のノード) を調整して変換を適用するか、ノードをそのままにしておくことができます。 その後、ノードを `Write` の関連する <xref:System.Xaml.XamlObjectWriter> API に送り、オブジェクトを書き込みます。 詳細については、「 [XAML ノード ストリームの構造と概念について](understanding-xaml-node-stream-structures-and-concepts.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [XAML サービス](index.md)

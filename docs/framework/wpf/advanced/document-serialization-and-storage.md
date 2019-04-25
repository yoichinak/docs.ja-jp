---
title: ドキュメントのシリアル化および保存
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: dbc78db0a3b6763af5270840fc56af648c7c6efc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295901"
---
# <a name="document-serialization-and-storage"></a>ドキュメントのシリアル化および保存
Microsoft .NET Framework では、作成して、高品質のドキュメントを表示するための強力な環境を提供します。  固定ドキュメントとフロー ドキュメント、詳細の両方をサポートする拡張機能は強力な 2D と組み合わせて表示コントロール、および 3D グラフィックス機能を .NET Framework アプリケーションの品質とユーザー エクスペリエンスの新しいレベルをします。  .NET Framework の主な機能は、ドキュメントのメモリ内表現を柔軟に管理できることと、ほとんどすべてのアプリケーションの必要があることを効率的に保存し、データ ストアからドキュメントを読み込みます。  内部のメモリ内表現から外部のデータ ストアにドキュメントを変換するプロセスは、シリアル化と呼ばれます。  データ ストアを読み取って元のメモリ内インスタンスを再作成する逆のプロセスは、逆シリアル化と呼ばれます。  

<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>ドキュメントのシリアル化について  
 ドキュメントをメモリからシリアル化し、後で逆シリアル化してメモリに戻すプロセスは、アプリケーションに対して透過的に行われるのが理想的です。  アプリケーションは、シリアライザーの "書き込み" メソッドを呼び出してドキュメントを保存します。デシリアライザーの "読み取り" メソッドは、データ ストアにアクセスし、メモリ内の元のインスタンスを再作成します。  通常、シリアル化と逆シリアル化のプロセスで元の形式のドキュメントが再作成される限り、データが格納される特定の形式はアプリケーションにとって問題ではありません。  
  
 多くの場合、アプリケーションでは複数のシリアル化オプションが提供され、ユーザーは異なるメディアまたは異なる形式にドキュメントを保存できます。  たとえば、[名前を付けて保存] オプションでは、ドキュメントをディスク ファイル、データベース、Web サービスなどに保存できる場合があります。  同様に、別のシリアライザーでは、HTML、RTF、XML、XPS、サード パーティ形式などのさまざまな形式でドキュメントを格納できます。  アプリケーションに対して、シリアル化により、実装内のストレージ メディアの詳細を分離するインターフェイスが定義されます。  ストレージの詳細は、.NET Framework をカプセル化することの利点に加え<xref:System.Windows.Documents.Serialization>[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]他のいくつかの重要な機能を提供します。  
  
### <a name="features-of-net-framework-30-document-serializers"></a>.NET Framework 3.0 ドキュメント シリアライザーの機能  
  
-   上位レベルのドキュメント オブジェクト (論理ツリーとビジュアル) に直接アクセスすることにより、ページ分割されたコンテンツ、2D/3D 要素、イメージ、メディア、ハイパーリンク、注釈、およびその他のサポート コンテンツの効率的な保存が可能になります。  
  
-   同期操作と非同期操作。  
  
-   拡張機能でのプラグイン シリアライザーのサポート:  
  
    -   すべての .NET Framework アプリケーションで使用するためのシステム全体のアクセス。  
  
    -   簡単なアプリケーション プラグインの検出。  
  
    -   カスタム サードパーティ プラグインの簡単な展開、インストール、更新。  
  
    -   カスタム実行時設定とオプションのユーザー インターフェイス サポート。  
  
### <a name="xps-print-path"></a>XPS 印刷パス  
 Microsoft .NET Framework[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]印刷パスには、印刷出力によってドキュメントを作成するための拡張機構も用意されています。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] は、ドキュメント ファイル形式と、[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] のネイティブ印刷スプール形式の両方として機能します。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] のドキュメントは [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 互換性のあるプリンターに直接送信でき、中間形式に変換する必要はありません。  印刷パス出力オプションと機能について詳しくは、「[印刷の概要](printing-overview.md)」をご覧ください。  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>プラグイン シリアライザー  
 <xref:System.Windows.Documents.Serialization> Api は、プラグイン シリアライザーと、アプリケーションから個別にインストールされているリンクされたシリアライザーの両方のサポートを提供し、実行時に、バインドを使用してアクセス、<xref:System.Windows.Documents.Serialization.SerializerProvider>検出メカニズム。  プラグイン シリアライザーには、簡単に展開でき、システム全体で使用できるという大きな利点があります。  プラグイン シリアライザーにアクセスできない [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] などの部分信頼環境には、リンクされたシリアライザーを実装することもできます。  派生実装に基づいて、シリアライザーのリンクされた、<xref:System.Windows.Documents.Serialization.SerializerWriter>クラスではコンパイルされ、アプリケーションに直接リンクします。  プラグイン シリアライザーとリンクされたシリアライザーはどちらも同じパブリック メソッドとイベントを通じて動作するので、同じアプリケーションでどちらか一方でも両方のシリアライザーでも簡単に使うことができます。  
  
 アプリケーション開発者にとっての利点として、プラグイン シリアライザーは新しいストレージ設計およびファイル形式に対する拡張性を備え、ビルド時に可能性のあるすべての形式を直接コーディングする必要はありません。  また、サードパーティの開発者にとっても、プラグイン シリアライザーには、カスタムまたは独自のファイル形式のためのシステムでアクセス可能なプラグインを展開、インストール、更新する標準化された手段が提供されるというメリットがあります。  
  
### <a name="using-a-plug-in-serializer"></a>プラグイン シリアライザーの使用  
 プラグイン シリアライザーは簡単に使うことができます。  <xref:System.Windows.Documents.Serialization.SerializerProvider>クラスを列挙、<xref:System.Windows.Documents.Serialization.SerializerDescriptor>オブジェクトの各プラグインがシステムにインストールします。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A>プロパティがインストールされているプラグインが現在の構成に基づくフィルター処理し、シリアライザーの読み込まれ、アプリケーションで使用されることを確認します。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor>もなどの他のプロパティを提供します<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A>と<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>シリアライザーを使用可能な出力形式を選択する際にユーザー入力を求めるアプリケーションを使用できます。  既定のプラグイン シリアライザー[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]は .NET Framework で提供されており、常に列挙されます。  ユーザーが、出力形式を選択した後、<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>メソッドの使用を作成、<xref:System.Windows.Documents.Serialization.SerializerWriter>の特定の形式。  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> データ ストアにドキュメント ストリームを出力するメソッドを呼び出すしできます。  
  
 次の例では、使用するアプリケーション、 <xref:System.Windows.Documents.Serialization.SerializerProvider> "PlugInFileFilter"プロパティのメソッド。  PlugInFileFilter はインストールされているプラグインを列挙し、フィルター文字列を使用可能なファイルのオプションを付けて、<xref:Microsoft.Win32.SaveFileDialog>します。  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 使用は次の例を示しています、ユーザーが、出力ファイル名を選択すると後、<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>指定された形式で指定されたドキュメントを格納する方法。  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>プラグイン シリアライザーのインストール  
 <xref:System.Windows.Documents.Serialization.SerializerProvider>クラスは、プラグイン シリアライザーを検出およびアクセスを上位のアプリケーション インターフェイスを提供します。  <xref:System.Windows.Documents.Serialization.SerializerProvider> 検索し、アプリケーションがインストールされ、システムでアクセスできるシリアライザーの一覧を示します。  インストールされているシリアライザーの詳細は、レジストリ設定によって定義されます。  プラグイン シリアライザーを使用して、レジストリに追加できる、<xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A>メソッドまたはレジストリ値自体で .NET Framework がまだない場合、インストールされているプラグインのインストール スクリプトを直接設定できます。  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A>以前にインストールされたを削除するメソッドを使用できるプラグイン、またはレジストリ設定は、アンインストール スクリプトで同様にリセットすることができます。  
  
### <a name="creating-a-plug-in-serializer"></a>プラグイン シリアライザーの作成  
 プラグイン シリアライザーとリンクされたシリアライザーはどちらも、同じ公開されたパブリック メソッドとイベントを使い、同期または非同期で動作するように同じように設計できます。  通常、プラグイン シリアライザーの作成には 3 つの基本的な手順があります。  
  
1. 最初に、シリアライザーをリンクされたシリアライザーとして実装してデバッグします。  コンパイルしてテスト アプリケーションに直接リンクするシリアライザーを最初に作成すると、テストに役立つブレークポイントや他のデバッグ サービスに完全にアクセスできます。  
  
2. シリアライザーを完全にテストした後、<xref:System.Windows.Documents.Serialization.ISerializerFactory>プラグインを作成するインターフェイスを追加します。  <xref:System.Windows.Documents.Serialization.ISerializerFactory>インターフェイスは、論理ツリーが含まれるすべての .NET Framework オブジェクトへのフル アクセスを許可<xref:System.Windows.UIElement>オブジェクト、 <xref:System.Windows.Documents.IDocumentPaginatorSource>、および<xref:System.Windows.Media.Visual>要素。  さらに<xref:System.Windows.Documents.Serialization.ISerializerFactory>同じ同期および非同期のメソッドとリンクされたシリアライザーで使用されるイベントを提供します。  サイズの大きいドキュメントの出力には時間がかかる場合があるため、ユーザーの操作に応答できる状態を維持し、データ ストアで問題が発生した場合の "キャンセル" オプションを提供できるよう、非同期操作を使うことをお勧めします。  
  
3. プラグイン シリアライザーを作成した後、プラグインを配布してインストール (およびアンインストール) するためのインストール スクリプトを実装します (前の「[プラグイン シリアライザーのインストール](#InstallingPluginSerializers)」を参照)。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
- [XML Paper Specification:概要](https://go.microsoft.com/fwlink?LinkID=106246)

---
title: 既定の XAML スキーマ コンテキストと WPF XAML スキーマ コンテキスト
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 0d6a0aa80d8490c509fa9036f88d4f6863ff040c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295602"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>既定の XAML スキーマ コンテキストと WPF XAML スキーマ コンテキスト
XAML スキーマ コンテキストとは、特定の XAML ボキャブラリを使用する XAML の運用環境とやり取りする方法などの型のマッピングが解決する方法、アセンブリが読み込まれる方法、特定のリーダーとライターの動作を記述するオブジェクトを修飾するエンティティの概念設定が解釈されます。 このトピックでは、.NET Framework XAML サービスと CLR 型システムに基づく関連付けられた既定の XAML スキーマ コンテキストの機能について説明します。 このトピックでは、WPF に使用される XAML スキーマ コンテキストにも説明します。  
  
## <a name="default-xaml-schema-context"></a>既定の XAML スキーマ コンテキスト  
 .NET framework XAML サービス実装し、既定の XAML スキーマ コンテキストが使用されます。 既定の XAML スキーマ コンテキストの動作が常の API に完全に表示されない、<xref:System.Xaml.XamlSchemaContext>クラス。 ただし、多くの場合、既定の XAML スキーマ コンテキストの影響を与える動作は、観測可能なオブジェクトのメンバーなど、XAML 型システムの一般的な API を介して<xref:System.Xaml.XamlMember>または<xref:System.Xaml.XamlType>、または XAML リーダーと XAML ライターを使用しているので公開されている Api を使用既定の XAML スキーマ コンテキスト。  
  
 作成することができます、<xref:System.Xaml.XamlSchemaContext>を呼び出すことによって、既定の動作をカプセル化、<xref:System.Xaml.XamlSchemaContext>コンス トラクター。 これにより、既定の XAML スキーマ コンテキストを明示的に作成されます。 XAML リーダーまたは XAML ライターを明示的に考慮していない Api を使用して初期化する場合、同じ既定の XAML スキーマ コンテキストが暗黙的に、作成、<xref:System.Xaml.XamlSchemaContext>入力パラメーター。  
  
 既定の XAML スキーマ コンテキストでは、その型のマッピングの動作の CLR リフレクションに依存しています。 これは、定義の CLR を調べることが含まれています。 <xref:System.Type>、および関連<xref:System.Reflection.PropertyInfo>または<xref:System.Reflection.MethodInfo>します。 また、型またはメンバーの CLR 属性は、XAML の型または型のバッキング CLR を使用する XAML メンバー情報の詳細を入力するために使用されます。 既定の XAML スキーマ コンテキストではなどの型システムの拡張手法は必要ありません、`Invoker`パターン、CLR 型システムから必要な情報があるためです。  
  
 アセンブリのロジックを読み込み、既定の XAML スキーマ コンテキストは主に XAML 名前空間のマッピングで提供されるすべてのアセンブリ値に依存します。 また、<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>アセンブリを読み込むには、内部型の読み込みなどのシナリオにヒントことができます。  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML スキーマ コンテキスト  
 WPF XAML スキーマ コンテキストが WPF 実装は、既定以外の XAML スキーマ コンテキストを実装することによってもたらされる機能の種類の興味深い例を提供するため、このトピックで説明します。 また、XAML スキーマ コンテキストの概念については説明しません非常に WPF XAML; に対応する WPF のドキュメントXAML スキーマ コンテキストができるようにする動作は、既定の XAML スキーマ コンテキストの動作の詳細については統合されている場合に、完全に理解できるもののみ場合があります。 WPF XAML スキーマ コンテキストでは、次の動作を実装します。  
  
 **参照の上書き:** WPF XAML のいくつかのコンテンツ モデルを持つせずに機能する XAML コンテンツ プロパティが<xref:System.Windows.Markup.ContentPropertyAttribute>に起因します。 <xref:System.Xaml.XamlType.LookupContentProperty%2A> WPF のオーバーライドでは、この動作を実装します。  
  
 **WPF の式の遅延:** WPF には、ランタイム コンテキストが利用可能になるまでの値を延期するいくつかの式クラスが機能します。 また、テンプレートの拡張は、遅延の手法に依存しているランタイムの動作です。  
  
 **システム参照の最適化を入力します。** WPF が、広範な XAML ボキャブラリとオブジェクト モデル、文字通り何百もの WPF 定義のクラスを継承する基底クラス メンバーの定義を含むです。 また、WPF 自体は複数のアセンブリに分散します。 WPF では、参照テーブルとその他の手法を使用してその型の参照を最適化します。 これは、既定の XAML スキーマ コンテキストとそのタイプの CLR ベースのルックアップのパフォーマンスの向上を提供します。 場所の種類に存在しない参照テーブルの場合、動作は、既定の XAML スキーマ コンテキストに類似した XAML スキーマ コンテキストのテクニックを使用します。  
  
 **XamlType と XamlMember の拡張機能:** WPF では、依存関係プロパティを持つプロパティの概念とルーティング イベントとイベントの概念を拡張します。 これらの概念に XAML 処理操作の可視性を与える、WPF を拡張<xref:System.Xaml.XamlType>と<xref:System.Xaml.XamlMember>、依存関係プロパティを報告し、イベントの特性をルーティングする内部プロパティを追加します。  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>WPF XAML スキーマ コンテキストにアクセスします。  
 WPF に基づく XAML 手法を使用しているかどうかは<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>または<xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>、WPF XAML スキーマ コンテキストは既にこれらの XAML リーダーと XAML ライターの実装に使用されています。  
  
 他の XAML リーダーまたは XAML ライターの実装を初期化しないを使用して、WPF XAML スキーマ コンテキストを使用している場合は、作業 WPF XAML スキーマ コンテキストを取得することがありますできます<xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>します。 使用するその他の API の初期化としてこの値を使用できますし、<xref:System.Xaml.XamlSchemaContext>します。 たとえば、呼び出すことができます<xref:System.Xaml.XamlXmlReader.%23ctor%2A>の初期化と WPF XAML スキーマ コンテキストを渡します。 または、XAML 型システムの操作、WPF XAML スキーマ コンテキストを使用する可能性があります。 構築の初期化があります、<xref:System.Xaml.XamlType>または<xref:System.Xaml.XamlMember>、または呼び出し<xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>します。  
  
 WPF XAML の特定の側面は、純粋な XAML ノード ストリームの観点からアクセスする場合、WPF フレームワークの機能のいくつかの可能性がありますが処理しなかったまだに注意してください。 たとえば、コントロール用の WPF テンプレートはまだ適用されません。 そのため、実行時に完全なビジュアル ツリーに挿入される場合をプロパティにアクセスする可能性がありますのみが表示テンプレートを参照するプロパティの値。 WPF のマークアップ拡張機能の提供サービスのコンテキストでは、できない可能性がありますも、非ランタイム状況から提供されている場合は、正確と、オブジェクト グラフを書き込もうとしているときに例外が発生できます。  
  
## <a name="xaml-and-assembly-loading"></a>XAML およびアセンブリの読み込み  
 アセンブリの XAML と .NET Framework XAML サービスの読み込みと統合の CLR で定義された概念<xref:System.AppDomain>します。 XAML スキーマ コンテキストにアセンブリを読み込むかの使用状況に基づいて実行時またはデザイン時に、型を検索する方法が解釈される<xref:System.AppDomain>およびその他の要因です。 ロジック、XAML が XAML リーダーの loose XAML がかどうかによって多少異なりますが、XAML での DLL にコンパイル`XamlBuildTask`、WPF のによって生成された BAML または`PresentationBuildTask`します。  
  
 WPF の XAML スキーマ コンテキストを使用して、WPF アプリケーション モデルと統合<xref:System.AppDomain>WPF 実装の詳細については、その他の要因とします。  
  
#### <a name="xaml-reader-input-loose-xaml"></a>XAML リーダーの入力 (loose XAML)  
  
1. 反復処理、XAML スキーマ コンテキスト、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、アプリケーションのアセンブリを読み込む最近最もから開始します。 一致が見つかった場合は、そのアセンブリが解決に使用します。  
  
2. CLR、次の手法のいずれかに基づいてそれ以外の場合、 <xref:System.Reflection.Assembly> API の使用は、アセンブリを読み込みます。  
  
    -   マッピングの名前を修飾すると場合、によって呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
    -   前の手順に失敗した場合は、短い名前 (および存在する場合の公開キー トークン) を使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>します。  
  
    -   名前で修飾のマッピングでない場合は、呼び出す<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>します。  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` Windows Communication Foundation (WCF) および Windows Workflow Foundation の使用されます。  
  
 アセンブリを参照するメモ`XamlBuildTask`は、常に完全修飾します。  
  
1. 呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
2. 前の手順に失敗した場合は、短い名前 (および存在する場合の公開キー トークン) を使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>します。  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 BAML のアセンブリの読み込みに 2 つの側面があります: コンポーネントとして BAML を含む初期アセンブリの読み込みと運用環境の BAML によって参照される任意の型の型のバッキング アセンブリを読み込みます。  
  
##### <a name="assembly-load-for-initial-markup"></a>初期のマークアップのアセンブリの読み込み:  
 マークアップを読み込むアセンブリへの参照は、常に修飾されません。  
  
1. 反復処理、WPF XAML スキーマ コンテキスト、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、WPF アプリケーションのアセンブリを読み込む最近最もから開始します。 一致が見つかった場合は、そのアセンブリが解決に使用します。  
  
2. 前の手順に失敗した場合は、短い名前 (および存在する場合の公開キー トークン) を使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>します。  
  
##### <a name="assembly-references-by-baml-types"></a>BAML 型でアセンブリ参照:  
 BAML 運用環境で使用される型のアセンブリ参照は、ビルド タスクの出力として、完全修飾では常にします。  
  
1. 反復処理、WPF XAML スキーマ コンテキスト、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、WPF アプリケーションのアセンブリを読み込む最近最もから開始します。 一致が見つかった場合は、そのアセンブリが解決に使用します。  
  
2. それ以外の場合、アセンブリを読み込む、次の手法のいずれかを使用します。  
  
    -   呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
    -   短い名前 + パブリック キー トークンの組み合わせ、BAML から読み込まれたアセンブリと同じでは、場合は、そのアセンブリを使用します。  
  
    -   短い名前と公開キー トークンを使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>します。  
  
## <a name="see-also"></a>関連項目

- [XAML ノード ストリームの構造と概念について](understanding-xaml-node-stream-structures-and-concepts.md)

---
title: 基本要素の概要
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 7d52d951d4fa4df83bbcca6b4cb479e18e532d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141629"
---
# <a name="base-elements-overview"></a>基本要素の概要
のクラスの割合[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]が高いのは、SDK ドキュメントで一般的に基本要素クラスと呼ばれる 4 つのクラスから派生しています。 これらのクラスは<xref:System.Windows.UIElement>、 <xref:System.Windows.FrameworkElement> <xref:System.Windows.ContentElement>、 <xref:System.Windows.FrameworkContentElement>、 、 、 、 です。 クラス<xref:System.Windows.DependencyObject>は、両方<xref:System.Windows.UIElement>の共通の基本クラスであるため、関連しています。<xref:System.Windows.ContentElement>  

<a name="base_apis"></a>
## <a name="base-element-apis-in-wpf-classes"></a>WPF クラスの基本要素 API  
 両方<xref:System.Windows.UIElement>とも<xref:System.Windows.ContentElement>、多少<xref:System.Windows.DependencyObject>異なる経路を介してから派生しています。 このレベルでの分割は、ユーザー<xref:System.Windows.UIElement>インターフェイス<xref:System.Windows.ContentElement>での 使用方法や、アプリケーションでの用途を処理します。 <xref:System.Windows.UIElement>また、<xref:System.Windows.Media.Visual>クラス階層にも含まれています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Visual>では、独立した矩形スクリーン領域を定義することで、レンダリングフレームワークを提供します。 実際には、<xref:System.Windows.UIElement>大きなオブジェクト モデルをサポートする要素、四角形の画面領域として記述できる領域にレンダリングおよびレイアウトを行うことを目的とし、コンテンツ モデルが意図的により開いている場合は、要素の異なる組み合わせを可能にします。 <xref:System.Windows.ContentElement>はから<xref:System.Windows.Media.Visual>派生しません。そのモデルは<xref:System.Windows.ContentElement>、リーダーやビューアなど、他の何かによって消費され、要素を解釈して完全<xref:System.Windows.Media.Visual>な消費を[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]生成するということです。 特定<xref:System.Windows.UIElement>のクラスはコンテンツホストを意図しており、1つ以上<xref:System.Windows.ContentElement>のクラスのホスティングとレンダリングを提供<xref:System.Windows.Controls.DocumentViewer>します(そのようなクラスの例です)。 <xref:System.Windows.ContentElement>は、オブジェクト モデルがやや小さい要素の基本クラスとして使用され、より多くのアドレスを指定するテキスト、情報、または内で<xref:System.Windows.UIElement>ホストされるドキュメントコンテンツです。  
  
### <a name="framework-level-and-core-level"></a>フレームワークレベルとコアレベル  
 <xref:System.Windows.UIElement>の基本クラス<xref:System.Windows.FrameworkElement>として機能し、<xref:System.Windows.ContentElement>の基本クラスとして機能します<xref:System.Windows.FrameworkContentElement>。 この次のレベルのクラスの理由は、WPF フレームワーク レベルとは別の WPF コア レベルをサポートするためであり、この区分は、API をプレゼンテーション コア アセンブリとプレゼンテーション フレームワーク アセンブリ間で分割する方法にも存在します。 WPF フレームワーク レベルは、表示のためのレイアウト マネージャーの実装など、アプリケーションの基本的ニーズに対して、より完全なソリューションを提供します。 WPF コア レベルは、アセンブリの追加によるオーバーヘッドを引き起こすことなく [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の大部分を使用する方法を提供します。 これらのレベルの違いは、ほとんどの一般的なアプリケーション開発シナリオでは非常に重要ではなく、一般的に、API 全体を考慮[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]する必要があり、WPF フレームワーク レベルと WPF コア レベルの違いに関する問題はありません。 アプリケーション設計で WPF フレームワーク レベルの機能の大部分を置き換えることにした場合、たとえば開発中のソリューション全体に、独自の[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の構成およびレイアウトが既に実装されている場合には、これらのレベルの区分に関する理解が必要となる可能性があります。  
  
<a name="subclassing_elements"></a>
## <a name="choosing-which-element-to-derive-from"></a>派生元の要素を選択する  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を拡張したカスタム クラスを作成するための最も実際的な方法は、既存のクラス階層から必要な機能を可能な限り得ることのできる、いずれかの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスから派生させることです。 このセクションでは、継承元とするクラスの選択に役立つように、最も重要な要素クラスのうちの 3 つのクラスが提供する機能を示します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実際にはクラスから派生する一般的な理由の 1 つであるコントロールを実装する場合は、実用的なコントロール、コントロール ファミリの基本クラス、または少なくとも基本クラスから派生する<xref:System.Windows.Controls.Control>必要があります。 いくつかのガイドラインと実際の例については、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」を参照してください。  
  
 コントロールを作成しているのではなく、階層の上位にあるクラスから派生する必要がある場合は、各基本要素クラスに定義された特性に関するガイドを意図した、以下のセクションを参照してください。  
  
 から<xref:System.Windows.DependencyObject>派生するクラスを作成する場合は、次の機能を継承します。  
  
- <xref:System.Windows.DependencyObject.GetValue%2A>サポート<xref:System.Windows.DependencyObject.SetValue%2A>、および一般的なプロパティ システムのサポート。  
  
- 依存関係プロパティと、依存関係プロパティとして実装されている添付プロパティを使用する機能。  
  
 から<xref:System.Windows.UIElement>派生するクラスを作成する場合は、 によって提供される機能に加えて、次の<xref:System.Windows.DependencyObject>機能も継承します。  
  
- アニメーション化されたプロパティ値の基本的なサポート。 詳細については、「アニメーションの[概要](../graphics-multimedia/animation-overview.md)」を参照してください。  
  
- 基本的な入力イベントのサポートと、コマンド実行のサポート。 詳細については、「[入力の概要](input-overview.md)」および「[コマンド実行の概要](commanding-overview.md)」を参照してください。  
  
- レイアウト システムに情報を提供するためにオーバーライドできる仮想メソッド。  
  
 から<xref:System.Windows.FrameworkElement>派生するクラスを作成する場合は、 によって提供される機能に加えて、次の<xref:System.Windows.UIElement>機能も継承します。  
  
- スタイル設定とストーリーボードのサポート。 詳細については、「 および<xref:System.Windows.Style>[ストーリーボードの概要](../graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
- データ バインディングのサポート。 詳細については、「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。  
  
- 動的リソース参照のサポート。 詳しくは、「[XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)」を参照してください。  
  
- プロパティ値継承のサポート、および、データ バインディング、スタイル、またはレイアウトのフレームワークの実装などのフレームワーク サービスのプロパティに関する条件をレポートする場合に役立つ、メタデータ内の他のフラグ。 詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。  
  
- 論理ツリーの概念。 詳細については、「[WPF のツリー](trees-in-wpf.md)」を参照してください。  
  
- レイアウトに影響を与えるプロパティの変更を検出できるオーバーライドを<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>含む、レイアウト システムの実用的な WPF フレームワーク レベルの実装のサポート。  
  
 から<xref:System.Windows.ContentElement>派生するクラスを作成する場合は、 によって提供される機能に加えて、次の<xref:System.Windows.DependencyObject>機能も継承します。  
  
- アニメーションのサポート。 詳細については、「アニメーションの[概要](../graphics-multimedia/animation-overview.md)」を参照してください。  
  
- 基本的な入力イベントのサポートと、コマンド実行のサポート。 詳細については、「[入力の概要](input-overview.md)」および「[コマンド実行の概要](commanding-overview.md)」を参照してください。  
  
 から<xref:System.Windows.FrameworkContentElement>派生するクラスを作成すると、 によって提供される機能に加えて、次の機能が<xref:System.Windows.ContentElement>利用できます。  
  
- スタイル設定とストーリーボードのサポート。 詳細については、「 および<xref:System.Windows.Style>[アニメーションの概要](../graphics-multimedia/animation-overview.md)」を参照してください。  
  
- データ バインディングのサポート。 詳細については、「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。  
  
- 動的リソース参照のサポート。 詳しくは、「[XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)」を参照してください。  
  
- プロパティ値継承のサポート、および、データ バインディング、スタイル、またはレイアウトのフレームワークの実装などのフレームワーク サービスのプロパティに関する条件をレポートする場合に役立つ、メタデータ内の他のフラグ。 詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。  
  
- レイアウト システムの変更 (など<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>) へのアクセスは継承されません。 レイアウト システムの実装は、<xref:System.Windows.FrameworkElement>でのみ使用できます。 ただし、レイアウトに影響<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>を与えるプロパティの変更を検出し、コンテンツ ホストにレポートできるオーバーライドを継承します。  
  
 さまざまなクラスに関してコンテンツ モデルがドキュメント化されています。 派生元として適切なクラスを見つける必要がある場合、クラスのコンテンツ モデルは、考慮する必要がある項目の候補の 1 つです。 詳細については、「[WPF のコンテンツ モデル](../controls/wpf-content-model.md)」を参照してください。  
  
<a name="other_base_classes"></a>
## <a name="other-base-classes"></a>他の基本クラス  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject>スレッド モデルの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]サポートを提供し、アプリケーション用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に作成されたすべてのオブジェクトを<xref:System.Windows.Threading.Dispatcher>に関連付けできます。 <xref:System.Windows.UIElement>から派生していない場合でも、<xref:System.Windows.DependencyObject><xref:System.Windows.Media.Visual>このスレッド モデル<xref:System.Windows.Threading.DispatcherObject>のサポートを得るために派生元を検討する必要があります。 詳細については、「[スレッド モデル](threading-model.md)」を参照してください。  
  
### <a name="visual"></a>ビジュアル  
 <xref:System.Windows.Media.Visual>は、通常、ほぼ四角形の領域で視覚的な表示を必要とする 2D オブジェクトの概念を実装します。 実際のレンダリングは他<xref:System.Windows.Media.Visual>のクラスで行われますが (自己完結型ではありません)、<xref:System.Windows.Media.Visual>クラスはさまざまなレベルでレンダリングプロセスで使用される既知の型を提供します。 <xref:System.Windows.Media.Visual>はヒット テストを実装しますが、ヒット テストの陽性を報告するイベントは公開しません<xref:System.Windows.UIElement>(これらは にあります)。 詳細については、「[ビジュアル層のプログラミング](../graphics-multimedia/visual-layer-programming.md)」を参照してください。  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable>変更できないオブジェクトが必要な場合や、パフォーマンス上の理由から必要な場合にオブジェクトのコピーを生成する手段を提供することにより、変更可能なオブジェクトの不変性をシミュレートします。 この<xref:System.Windows.Freezable>タイプは、ジオメトリやブラシなどの特定のグラフィックス要素やアニメーションに共通の基礎を提供します。 特に、a<xref:System.Windows.Freezable>は、 <xref:System.Windows.Media.Visual>このプロパティは、 が<xref:System.Windows.Freezable>適用されて別のオブジェクトのプロパティ値が埋め込まれるときにサブプロパティになるプロパティを保持でき、それらのサブプロパティがレンダリングに影響する場合があります。 詳細については、「[Freezable オブジェクトの概要](freezable-objects-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>は、<xref:System.Windows.Freezable>アニメーション コントロール レイヤと一部のユーティリティ メンバを追加する派生クラスであり、現在アニメーション化されているプロパティをアニメーション化されていないプロパティと区別できるようにします。  
  
### <a name="control"></a>コントロール  
 <xref:System.Windows.Controls.Control>は、テクノロジに応じて、コントロールまたはコンポーネントと呼ばれますさまざまなオブジェクトの型の目的の基本クラスです。 一般に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール クラスは、UI コントロールを直接表すクラスか、コントロールの複合に密接に参加するクラスです。 有効にする<xref:System.Windows.Controls.Control>主な機能は、コントロール テンプレートです。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Control>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
- [WPF アーキテクチャ](wpf-architecture.md)

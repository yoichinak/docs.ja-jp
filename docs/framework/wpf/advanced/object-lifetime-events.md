---
title: オブジェクトの有効期間イベント
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: 3b761674bd2464ee87e07d9299c805431f8fdeb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141108"
---
# <a name="object-lifetime-events"></a>オブジェクトの有効期間イベント
このトピックでは、オブジェクトの有効期間における作成、使用、破棄のステージを示す特定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントについて説明します。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](dependency-properties-overview.md)」というトピックを読んでいることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] について理解し (「[XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)」を参照)、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述方法を理解していることも必要です。  
  
<a name="intro"></a>
## <a name="object-lifetime-events"></a>オブジェクトの有効期間イベント  
 Microsoft .NET Framework マネージ コードのすべてのオブジェクトは、ライフ、作成、使用、および破棄の類似した一連のステージを通過します。 また、多くのオブジェクトには、破棄フェーズの一環として発生する有効期間の終了ステージもあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクト (具体的には [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が要素として識別するビジュアル オブジェクト) にも、共通する一連のオブジェクト有効期間ステージがあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プログラミングおよびアプリケーション モデルでは、これらのステージが一連のイベントとして公開されます。 有効期間イベントに関しては、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に、全般的要素、ウィンドウ要素、ナビゲーション ホスト、アプリケーション オブジェクトの 4 種類の主要オブジェクトがあります。 ウィンドウ要素とナビゲーション ホストは、さらに大きなビジュアル オブジェクト (要素) のグループにも含まれます。 このトピックでは、すべての要素に共通する有効期間イベントについて説明し、次にアプリケーション定義、ウィンドウ要素、またはナビゲーション ホストに適用される特定の有効期間イベントについて説明します。  
  
<a name="common_events"></a>
## <a name="common-lifetime-events-for-elements"></a>要素に関する共通の有効期間イベント  
 WPF<xref:System.Windows.FrameworkElement>フレームワーク レベルの要素 ( または<xref:System.Windows.FrameworkContentElement>のいずれかから派生するオブジェクト ) には<xref:System.Windows.FrameworkElement.Initialized>、 <xref:System.Windows.FrameworkElement.Loaded>、、および<xref:System.Windows.FrameworkElement.Unloaded>の 3 つの一般的な有効期間イベントがあります。  
  
### <a name="initialized"></a>初期化済み  
 <xref:System.Windows.FrameworkElement.Initialized>は最初に発生し、コンストラクターの呼び出しによるオブジェクトの初期化とほぼ一致します。 このイベントは初期化に応答して発生するため、オブジェクトのすべてのプロパティが設定されることが保証されます。 (例外は、動的リソースやバインディングなどの式の使用法であり、これらは評価されていない式です。すべてのプロパティが設定<xref:System.Windows.FrameworkElement.Initialized>されるという要件の結果として、マークアップで定義された入れ子になった要素によって発生する順序は、最初に要素ツリー内の最も深い要素の順序で発生し、次にルートに向かって親要素が発生するように見えます。 この順序に従うのは、親子のリレーションシップおよびコンテインメントがプロパティであるためです。その結果、親のプロパティを設定する子要素も完全に初期化されるまで、親は初期化を報告できません。  
  
 イベントに応答してハンドラーを<xref:System.Windows.FrameworkElement.Initialized>記述する場合、ハンドラーがアタッチされている要素ツリー (論理ツリーまたはビジュアル ツリー) 内の他のすべての要素 (特に親要素) が作成されたことを保証するものは存在しない必要があります。 メンバー変数が null である可能性や、基になるバインディングによってデータ ソースがまだ設定されていない可能性があります (式レベルでも)。  
  
### <a name="loaded"></a>読み込み  
 <xref:System.Windows.FrameworkElement.Loaded>次に上げられます。 イベント<xref:System.Windows.FrameworkElement.Loaded>は最終的なレンダリングの前に発生しますが、レイアウト システムがレンダリングに必要なすべての値を計算した後です。 <xref:System.Windows.FrameworkElement.Loaded>要素が含まれている論理ツリーが完成し、HWND とレンダリング サーフェイスを提供するプレゼンテーション ソースに接続します。 標準データ バインディング (他のプロパティや直接定義されたデータ ソースなど、ローカル ソースへのバインド)<xref:System.Windows.FrameworkElement.Loaded>は、 より前に行われます。 非同期データ バインディング (外部ソースまたは動的ソース) が発生する可能性もありますが、非同期であるという性質の定義から、その保証はできません。  
  
 <xref:System.Windows.FrameworkElement.Loaded>イベントが発生するメカニズムは、 とは<xref:System.Windows.FrameworkElement.Initialized>異なります。 イベント<xref:System.Windows.FrameworkElement.Initialized>は要素ごとに発生し、完了した要素ツリーによって直接調整されません。 対照的に<xref:System.Windows.FrameworkElement.Loaded>、イベントは要素ツリー全体 (具体的には論理ツリー) 全体にわたって協調的な作業として発生します。 ツリー内のすべての要素が読み込み済みと見なされる状態の<xref:System.Windows.FrameworkElement.Loaded>場合、イベントは最初にルート要素で発生します。 イベント<xref:System.Windows.FrameworkElement.Loaded>は、各子要素で連続して発生します。  
  
> [!NOTE]
> この動作は、表面上は、ルーティング イベントのトンネリングに似ているとも言えます。 ただし、イベントからイベントへと伝達される情報はありません。 各要素には常にその<xref:System.Windows.FrameworkElement.Loaded>イベントを処理する機会があり、イベント データを処理済みとしてマークしても、その要素以外の効果はありません。  
  
### <a name="unloaded"></a>アンロードされました  
 <xref:System.Windows.FrameworkElement.Unloaded>は最後に発生し、削除されるプレゼンテーション ソースまたはビジュアル親によって開始されます。 イベント<xref:System.Windows.FrameworkElement.Unloaded>ソースの親である要素 (プロパティによって決定される<xref:System.Windows.FrameworkElement.Parent%2A>) または論理ツリーまたはビジュアル ツリー内の特定の要素が既に設定されていない可能性があります。  
  
<a name="application_model_elements"></a>
## <a name="lifetime-events-application-model-elements"></a>有効期間イベント アプリケーション モデルの要素  
 要素の一般的な有効期間イベントに基づいて構築されるアプリケーション モデル<xref:System.Windows.Application>要素<xref:System.Windows.Window>、 <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>、、および 。 これらの要素は、共通の有効期間イベントを拡張して、特定の目的に関連するイベントを追加します。 これらの詳細については、次のトピックで説明しています。  
  
- <xref:System.Windows.Application>:[アプリケーション管理の概要](../app-development/application-management-overview.md)  
  
- <xref:System.Windows.Window>: [WPF ウィンドウの概要](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>、<xref:System.Windows.Controls.Frame>および :[ナビゲーションの概要](../app-development/navigation-overview.md)。  
  
## <a name="see-also"></a>関連項目

- [依存関係プロパティの値の優先順位](dependency-property-value-precedence.md)
- [ルーティング イベントの概要](routed-events-overview.md)

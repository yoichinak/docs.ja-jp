---
title: UI オートメーション ExpandCollapse コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 232bceba8286c2566a7df03b9001a5c43b348b20
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043453"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>UI オートメーション ExpandCollapse コントロール パターンの実装

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。

このトピックでは、プロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、概要の最後に記載します。

<xref:System.Windows.Automation.ExpandCollapsePattern> コントロール パターンは、視覚的に展開してより多くのコンテンツを表示したり、折りたたんでコンテンツを非表示にしたりするコントロールをサポートするために使用します。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則

ExpandCollapse コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。

- 展開または折りたたみの機能を備えた UI を提供する子オブジェクトで構成された集約コントロールは、 <xref:System.Windows.Automation.ExpandCollapsePattern> コントロール パターンをサポートする必要がありますが、その子要素がサポートする必要はありません。 たとえば、コンボ ボックス コントロールは、リスト ボックス、ボタン、およびエディット コントロールの組み合わせで構成されていますが、 <xref:System.Windows.Automation.ExpandCollapsePattern>をサポートする必要があるのは親のコンボ ボックスのみです。

  > [!NOTE]
  > メニュー コントロールは例外であり、これは個々の MenuItem オブジェクトの集合体です。 MenuItem オブジェクトは <xref:System.Windows.Automation.ExpandCollapsePattern> コントロール パターンをサポートできますが、親の Menu コントロールはできません。 同様の例外が、Tree および Tree Item コントロールにも適用されます。

- コントロールの <xref:System.Windows.Automation.ExpandCollapseState> が <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>に設定されている場合、コントロールに対して現在アクティブな <xref:System.Windows.Automation.ExpandCollapsePattern> 機能は存在せず、このコントロール パターンを使用して取得できる情報は <xref:System.Windows.Automation.ExpandCollapseState>だけです。 その後、子オブジェクトが追加された場合は、 <xref:System.Windows.Automation.ExpandCollapseState> が変更され、 <xref:System.Windows.Automation.ExpandCollapsePattern> 機能がアクティブになります。

- <xref:System.Windows.Automation.ExpandCollapseState> は、すべての子孫オブジェクトの可視性を表すのではなく、直接の子オブジェクトの可視性のみを表します。

- 展開および折りたたみ機能は、コントロールに固有の機能です。 この機能の動作例を次に示します。

  - Office Personal のメニューには、3 つの状態を示す MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>、 <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> 、および <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) を指定できます。この場合、 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> または <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> を呼び出したときに選択される状態は、コントロールによって指定されます。

  - TreeItem で <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> を呼び出すと、すべての子孫または直接の子のみを表示できます。

  - コントロールでの <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> または <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> の呼び出しによってその子孫の状態が維持されるとき、状態の変更イベントではなく、可視性の変更イベントが送信されます。折りたたみの実行時に親コントロールが子孫の状態を維持しないときは、コントロールが表示されなくなったすべての子孫を破棄し、破棄イベントを発生させる場合と、子孫ごとに <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> を変更して、可視性の変更イベントを発生させる場合があります。

- ナビゲーションを確実にするには、オブジェクトを親の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] に関係なく、(可視性の状態が適切な) <xref:System.Windows.Automation.ExpandCollapseState>ツリー内に配置することをお勧めします。 子孫が必要に応じて生成される場合、それらが [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーに表示されるのは、初回の表示以降か、または可視状態になっている間に限られます。

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>IExpandCollapseProvider の必須メンバー

<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>の実装には、次のプロパティとメソッドが必要です。

|必須メンバー|メンバーの型|メモ|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|プロパティ|なし|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|メソッド|なし|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|メソッド|なし|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|イベント|このコントロールには関連付けられているイベントがありません。この汎用デリゲートを使用します。|

<a name="Exceptions"></a>

## <a name="exceptions"></a>例外

プロバイダーは、次の例外をスローする必要があります。

|例外の型|条件|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|が<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>の<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>場合、または<xref:System.Windows.Automation.ExpandCollapseState>  = の<xref:System.Windows.Automation.ExpandCollapseState.LeafNode>いずれかが呼び出されます。|

## <a name="see-also"></a>関連項目

- [UI Automation コントロール パターンの概要](ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](ui-automation-control-patterns-for-clients.md)
- [TreeWalker を使用した UI オートメーション要素間の移動](navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Automation ツリーの概要](ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)

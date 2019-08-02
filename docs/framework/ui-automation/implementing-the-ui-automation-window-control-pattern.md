---
title: UI オートメーション Window コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: 9cab4dbbcd3302a6e74783eaefdbbd8463332224
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710252"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>UI オートメーション Window コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 このトピックでは、 <xref:System.Windows.Automation.Provider.IWindowProvider>のプロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.WindowPattern> の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 コントロール<xref:System.Windows.Automation.WindowPattern>パターンは、従来のグラフィカルユーザーインターフェイス (GUI) 内で、ウィンドウベースの基本的な機能を提供するコントロールをサポートするために使用されます。 このコントロール パターンを実装する必要があるコントロールの例として、最上位のアプリケーション ウィンドウ、 [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] 子ウィンドウ、サイズ変更可能な分割ウィンドウ コントロール、モーダル ダイアログ ボックス、バルーン ヘルプ ウィンドウがあります。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 Window コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。  
  
- UI オートメーションを使用してウィンドウのサイズと位置の両方を変更する機能をサポートするには、コントロールが <xref:System.Windows.Automation.Provider.ITransformProvider> に加えて <xref:System.Windows.Automation.Provider.IWindowProvider>を実装する必要があります。  
  
- コントロールを移動、サイズ変更、最大化、最小化、および閉じられるようにするタイトル バーの要素とタイトル バーを格納するコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装することが求められます。  
  
- ツールヒントのポップアップやコンボ ボックス、またはメニューのドロップダウンなどのコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装しません。  
  
- バルーン ヘルプ ウィンドウは、ウィンドウと同様の閉じるボタンを提供することで、基本的なツールヒント ポップアップから区別されます。  
  
- 全画面表示モードは、アプリケーション固有の機能であり、通常のウィンドウの動作ではないため、IWindowProvider によってサポートされません。  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>IWindowProvider の必須メンバー  
 IWindowProvider インターフェイスには、次のプロパティ、メソッド、イベントが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|イベント|なし|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|イベント|なし|  
|<xref:System.Windows.Automation.WindowInteractionState>|イベント|<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の型|条件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -要求された動作をコントロールがサポートしていない場合。|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -パラメーターが有効な数値でない場合。|  
  
## <a name="see-also"></a>関連項目

- [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)

---
title: UI オートメーション MultipleView コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 74e5908dfcd42d031464ffccedb530be4a71a3f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125199"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>UI オートメーション MultipleView コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IMultipleViewProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.MultipleViewPattern> コントロール パターンは、同じ情報セットまたは子コントロールの複数の表現を提供し、それらの表現を切り替えることができるコントロールをサポートするために使用します。  
  
 複数のビューを表示できるコントロールの例には、リスト ビュー (サムネイル、タイル、アイコン、または詳細の形でコンテンツを表示できる)、 [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] チャート (円、線、棒、式を含むセル値)、 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 文書 (標準、Web レイアウト、印刷レイアウト、閲覧レイアウト、アウトライン)、 [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] カレンダー (年、月、週、日)、 [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] スキンなどがあります。 サポートされるビューはコントロールの開発者によって決定され、各コントロールに固有です。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 Multiple View コントロール パターンを実装する場合は、次のガイドラインと規則にご注意ください。  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider> 現在のビューを提供するコントロールとは異なる場合は、現在のビューを管理するコンテナーにも実装する必要があります。 たとえば、Windows エクスプローラーには現在のフォルダーのコンテンツの List コントロールが含まれていますが、そのコントロールのビューは Windows エクスプローラーのアプリケーションから管理されています。  
  
-   自身のコンテンツを並べ替えることができるコントロールは、複数のビューをサポートしているとは見なされません。  
  
-   ビューのコレクションは、インスタンス間で同じである必要があります。  
  
-   ビューの名前は、読み上げ、ブライユ点字、その他の人間が判読できるアプリケーションでの使用に適した名前にする必要があります。  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>IMultipleViewProvider の必須メンバー  
 IMultipleViewProvider の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|メソッド|なし|  
  
 このコントロールのパターンに関連付けられているイベントはありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> または <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> が、サポートされているビュー コレクションのメンバーではないパラメーターで呼び出された場合。|  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI オートメーション ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)

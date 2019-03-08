---
title: UI オートメーション Value コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: 8a306fe648c42e1e94126f10b0d4c92f9dfc8831
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678076"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>UI オートメーション Value コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IValueProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.ValuePattern> コントロール パターンは、範囲にまたがることのない組み込み値を持つコントロールや、文字列として表すことができるコントロールをサポートするために使用されます。 この文字列は、コントロールとその設定によっては、編集できます。 このパターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 Value コントロール パターンを実装する場合は、次のガイドラインと規則に留意してください。  
  
-   <xref:System.Windows.Automation.ControlType.ListItem> や <xref:System.Windows.Automation.ControlType.TreeItem> などのコントロールは、コントロールの現在の編集モードに関係なく、いずれかの項目の値が編集可能である場合は、 <xref:System.Windows.Automation.ValuePattern> をサポートする必要があります。 子項目が編集可能である場合は、親コントロールも <xref:System.Windows.Automation.ValuePattern> をサポートする必要があります。  
  
 ![編集可能なリスト項目。](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
編集可能なリスト項目の例  
  
-   単一行のエディット コントロールは、そのコンテンツへのプログラムによるアクセスをサポートするために、 <xref:System.Windows.Automation.Provider.IValueProvider>を実装します。 一方、複数行のエディット コントロールは <xref:System.Windows.Automation.Provider.IValueProvider>を実装しません。代わりに <xref:System.Windows.Automation.Provider.ITextProvider>を実装して、そのコンテンツへのアクセスを提供します。  
  
-   複数行の編集コントロールのテキスト コンテンツを取得するには、コントロールが <xref:System.Windows.Automation.Provider.ITextProvider>を実装していなければなりません。 ただし、 <xref:System.Windows.Automation.Provider.ITextProvider> はコントロールの値の設定はサポートしていません。  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> は、書式設定情報や部分文字列の値の取得をサポートしていません。 このようなシナリオでは <xref:System.Windows.Automation.Provider.ITextProvider> を実装します。  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> を実装する必要があるコントロールの一例は、 **の** カラー ピッカー [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 選択コントロールです (以下を参照)。このコントロールは、色の値 (たとえば「黄」) と同等の内部 [!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)] 構造の間の文字列マッピングをサポートしています。  
  
 ![黄色が強調表示されたカラー ピッカー。](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
色見本の文字列のマッピング例  
  
-   <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> を呼び出せるようにするには、コントロールの `true` を <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> に設定し、 `false` を <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>に設定する必要があります。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>IValueProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.IValueProvider>の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|メソッド|なし|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> 場合、ロケールに固有の情報は、正しくない形式の日付などの形式が正しくないコントロールに渡されます。|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -新しい値は、文字列から形式に変換できない場合、コントロールを認識します。|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -しようとしましたが有効になっていないコントロールを操作します。|  
  
## <a name="see-also"></a>関連項目
- [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [ValuePattern 挿入テキスト サンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)

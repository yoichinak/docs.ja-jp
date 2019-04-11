---
title: WPF カスタム コントロールの UI オートメーション
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: 0d663acc195b36fdc95c196f2233ae997fbd9195
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132770"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF カスタム コントロールの UI オートメーション
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] クライアントを確認またはさまざまなプラットフォームやフレームワークのユーザー インターフェイスの操作に使用できる automation はその 1 つの汎用的なインターフェイスを提供します。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 品質保証 (テスト) コードとユーザー インターフェイス要素を確認し、他のコードからそれらにユーザーの操作をシミュレートするスクリーン リーダーなどのユーザー補助アプリケーションの両方を使用できます。 すべてのプラットフォームにまたがる [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] について詳しくは、「ユーザー補助機能」を参照してください。  
  
 このトピックでは、WPF アプリケーションで動作するカスタム コントロールのサーバー側 UI オートメーション プロバイダーを実装する方法について説明します。 WPF は、ユーザー インターフェイス要素のツリーに対応するピア オートメーション オブジェクトのツリーを使用して [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] をサポートします。 テスト コードおよびユーザー補助機能を提供するアプリケーションは、オートメーション ピア オブジェクトを直接 (プロセス内コードに対して)、または [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] が提供する汎用のインターフェイスを介して使用できます。  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>オートメーション ピア クラス  
 WPF のサポートを制御する[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]から派生するピア クラスのツリーを通じて<xref:System.Windows.Automation.Peers.AutomationPeer>します。 規則上、ピア クラス名は、コントロールのクラス名で始まり、"AutomationPeer" で終わります。 たとえば、<xref:System.Windows.Automation.Peers.ButtonAutomationPeer>のピア クラスには、<xref:System.Windows.Controls.Button>コントロール クラス。 ピア クラスは、[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] コントロール型とほぼ同等ですが、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素専用です。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] インターフェイスを介して WPF アプリケーションにアクセスするオートメーション コードは、オートメーション ピアを直接使用しませんが、同じプロセス空間のオートメーション コードは、オートメーション ピアを直接使用できます。  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>組み込みのオートメーション ピア クラス  
 要素は、ユーザーからのインターフェイス アクティビティを受け入れる場合、またはスクリーン リーダー アプリケーションのユーザーが必要とする情報が含まれている場合、オートメーション ピア クラスを実装します。 すべての WPF のビジュアル要素にオートメーション ピアがあるわけではありません。 オートメーション ピアを実装するクラスの例は、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.TextBox>、および<xref:System.Windows.Controls.Label>します。 オートメーション ピアを実装していないクラスの例は、クラスから派生した<xref:System.Windows.Controls.Decorator>など<xref:System.Windows.Controls.Border>、およびクラスに基づく<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.Grid>と<xref:System.Windows.Controls.Canvas>します。  
  
 基本<xref:System.Windows.Controls.Control>クラスには、対応するピア クラスがありません。 ピア クラスから派生したカスタム コントロールに対応する必要がある場合<xref:System.Windows.Controls.Control>からカスタム ピア クラスを派生させる必要があります<xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>します。  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>派生ピアのセキュリティに関する考慮事項  
 オートメーション ピアは、部分信頼環境で実行する必要があります。 UIAutomationClient アセンブリ内のコードは部分信頼環境で動作するように構成されていないため、オートメーション ピア コードでそのアセンブリを参照しないでください。 代わりに、UIAutomationTypes アセンブリのクラスを使用する必要があります。 たとえば、使用する必要があります、<xref:System.Windows.Automation.AutomationElementIdentifiers>クラスに対応する UIAutomationTypes アセンブリから、 <xref:System.Windows.Automation.AutomationElement> UIAutomationClient アセンブリ内のクラス。 オートメーション ピア コードで UIAutomationTypes アセンブリを参照すると安全です。  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>ピア ナビゲーション  
 オートメーション ピアを特定すると、プロセス内コードは、オブジェクトを呼び出すことによってピア ツリーを移動できます<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A>と<xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A>メソッド。 間のナビゲーション[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のピアの実装によって、コントロール内の要素がサポートされている、<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A>メソッド。 UI オートメーション システムは、このメソッドを呼び出して、コントロール内に含まれるサブ要素のツリーを構築します。たとえば、リスト ボックス内の項目を一覧表示します。 既定の<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType>メソッドは、オートメーション ピアのツリーを構築する要素のビジュアル ツリーを走査します。 カスタム コントロールは、このメソッドをオーバーライドして子要素をオートメーション クライアントに公開し、情報を伝達するまたはユーザーによる操作を許可する要素のオートメーション ピアを返します。  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>派生ピアのカスタマイズ  
 すべてのクラスから派生する<xref:System.Windows.UIElement>と<xref:System.Windows.ContentElement>、プロテクト仮想メソッドを含む<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>。 WPF 呼び出し<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>各コントロールのオートメーション ピア オブジェクトを取得します。 オートメーション コードは、ピアを使用して、コントロールの特性と機能に関する情報を取得し、対話型の使用をシミュレートします。 オートメーションをサポートするカスタム コントロールをオーバーライドする必要があります<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>から派生したクラスのインスタンスを返すと<xref:System.Windows.Automation.Peers.AutomationPeer>します。 たとえば、カスタム コントロールから派生、<xref:System.Windows.Controls.Primitives.ButtonBase>クラス、によって返されるオブジェクト<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>から派生する必要があります<xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>します。  
  
 カスタム コントロールを実装する場合、カスタム コントロールに固有の動作を説明する基本オートメーション ピア クラスからの「コア」メソッドをオーバーライドする必要があります。  
  
### <a name="override-oncreateautomationpeer"></a>OnCreateAutomationPeer のオーバーライド  
 上書き、<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>から直接または間接的に派生する必要があります、プロバイダー オブジェクトを返すように、カスタム コントロールのメソッドを<xref:System.Windows.Automation.Peers.AutomationPeer>します。  
  
### <a name="override-getpattern"></a>GetPattern のオーバーライド  
 オートメーション ピアは、サーバー側の [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] プロバイダーの実装の一部を簡略化しますが、カスタム コントロール オートメーション ピアでもパターン インターフェイスを処理する必要があります。 非 WPF プロバイダーと同様にピアがでインターフェイスの実装を提供することでコントロール パターンをサポート、<xref:System.Windows.Automation.Provider?displayProperty=nameWithType>名前空間など<xref:System.Windows.Automation.Provider.IInvokeProvider>します。 コントロール パターンのインターフェイスは、ピア自体または別のオブジェクトによって実装できます。 ピアの実装の<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>指定のパターンをサポートするオブジェクトを返します。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] コードの呼び出し、<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>メソッドを指定し、<xref:System.Windows.Automation.Peers.PatternInterface>列挙値。 オーバーライド<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>を指定したパターンを実装するオブジェクトを返す必要があります。 基本型の実装を呼び出すことができます、コントロールがカスタム パターンの実装を持たない場合<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>をこの種類のコントロールのパターンがサポートされていない場合、実装、または null のいずれかを取得します。 値の範囲内にカスタムの NumericUpDown コントロールを設定するなど、その[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]ピアを実装、<xref:System.Windows.Automation.Provider.IRangeValueProvider>インターフェイス。 次の例はどのようにピアの<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>に応答するメソッドをオーバーライド、<xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>値。  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>メソッドではサブ要素をパターン プロバイダーとしても指定できます。 次のコードはどのように<xref:System.Windows.Controls.ItemsControl>転送スクロール パターン処理の内部のピアに<xref:System.Windows.Controls.ScrollViewer>コントロール。  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 このコード パターン処理のサブ要素を指定するにはサブ要素オブジェクトを取得を使用してピアを作成、<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>メソッドを設定、<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>を現在のピアでは、新しいピアのプロパティを新しいピアを返します。 設定<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>サブ要素で、オートメーション ピア ツリーに表示されない、サブ要素を防止し、サブ要素によって生成されるすべてのイベントを指定で指定したコントロールからのものとして<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>します。 <xref:System.Windows.Controls.ScrollViewer>コントロールはオートメーション ツリーで表示されずから生成するスクロール イベントが表示されます、<xref:System.Windows.Controls.ItemsControl>オブジェクト。  
  
### <a name="override-core-methods"></a>「コア」メソッドのオーバーライド  
 オートメーション コードは、ピア クラスのパブリック メソッドを呼び出して、コントロールに関する情報を取得します。 コントロールに関する情報を提供するには、コントロールの実装が基本オートメーション ピア クラスで提供されているものとは異なる場合に、"Core" で終わる名前を持つ各メソッドをオーバーライドします。 少なくとも、コントロールを実装する必要があります、<xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A>と<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>メソッドは、次の例に示すようにします。  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 実装<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>を返すことによって、コントロールを説明する<xref:System.Windows.Automation.ControlType>値。 返すことができますが<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>コントロールを正確に説明されている場合より特定のコントロール型の 1 つ返す必要があります。 戻り値<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>、プロバイダーを実装するための追加作業が必要です[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]、および[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]クライアント製品は、コントロールの構造、キーボード操作、および可能なコントロール パターンを予測することはできません。  
  
 実装、<xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A>と<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>メソッドは、コントロールがデータの内容が含まれていますか (またはその両方) をユーザー インターフェイスで対話型のロールかどうかを示します。 既定では、両方のメソッドが `true` を返します。 これらの設定は、オートメーション ツリーをフィルター処理するこれらのメソッドを使用できるスクリーン リーダーなどのオートメーション ツールの使いやすさを向上します。 場合、 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> 、サブ要素ピアに、サブ要素ピアの処理メソッド転送パターン<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>メソッドは、オートメーション ツリーからのサブ要素ピアを非表示に false を返します。 などのスクロール、<xref:System.Windows.Controls.ListBox>によって処理されます、 <xref:System.Windows.Controls.ScrollViewer>、およびオートメーション ピアを<xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType>によって返される、<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>のメソッド、<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>関連付けられている、<xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>します。そのため、<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>のメソッド、<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>返します`false`するように、<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>オートメーション ツリーには表示されません。  
  
 オートメーション ピアは、コントロールに適切な既定値を提供する必要があります。 含めることによって、コントロールを参照する XAML がコア メソッドのピア実装をオーバーライドできることに注意してください<xref:System.Windows.Automation.AutomationProperties>属性。 たとえば、次の XAML は、カスタマイズされた [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] プロパティが 2 つあるボタンを作成します。  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>パターン プロバイダーの実装  
 所有している要素がから直接派生している場合に、カスタム プロバイダーによって実装されるインターフェイスが明示的に宣言される<xref:System.Windows.Controls.Control>します。 たとえば、次のコードがのピアを宣言、<xref:System.Windows.Controls.Control>範囲の値を実装します。  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 所有しているコントロールがなど特定の種類のコントロールから派生している場合<xref:System.Windows.Controls.Primitives.RangeBase>ピアは、同等の派生ピア クラスから派生できます。 この場合は、ピアはから派生が<xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>の基本実装を提供する<xref:System.Windows.Automation.Provider.IRangeValueProvider>します。 次のコードは、そのようなピアの宣言を示します。  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 実装の例は、「[NumericUpDown Custom Control with Theme and UI Automation Support Sample](https://go.microsoft.com/fwlink/?LinkID=160025)」を参照してください。  
  
### <a name="raise-events"></a>イベントを発生させる  
 オートメーション クライアントは、オートメーション イベントをサブスクライブできます。 カスタム コントロールが呼び出すことによってコントロールの状態に対する変更を報告する必要があります、<xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>メソッド。 同様に、プロパティ値が変化するときに呼び出す、<xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>メソッド。 次のコードは、コントロール コード内からピア オブジェクトを取得し、イベントを発生させるメソッドを呼び出す方法を示しています。 最適化として、このコードは、このイベント型のリスナーがいるかどうかを判断します。 リスナーがいる場合にのみイベントを発生させると、不要なオーバーヘッドを回避し、コントロールの応答性を維持できます。  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションの概要](../../ui-automation/ui-automation-overview.md)
- [NumericUpDown Custom Control with Theme and UI Automation Support Sample](https://go.microsoft.com/fwlink/?LinkID=160025)
- [サーバー側 UI オートメーション プロバイダーの実装](../../ui-automation/server-side-ui-automation-provider-implementation.md)

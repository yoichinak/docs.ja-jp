---
title: カスタム コントロールの UI オートメーション
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
ms.openlocfilehash: 97db94215220ac2a68e0395bd63b7a874a745a48
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243246"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF カスタム コントロールの UI オートメーション
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] は、オートメーション クライアントが使用してさまざまなプラットフォームやフレームワークのユーザー インターフェイスを調査または操作できる、単一の汎用的なインターフェイスを提供します。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] では、品質保証 (テスト) のコードとスクリーン リーダーなどのユーザー補助アプリケーションの両方を使用して、ユーザー インターフェイス要素を調べて、他のコードからその要素を使用してユーザーの操作をシュミレーションできます。 すべてのプラットフォームにまたがる [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] について詳しくは、「ユーザー補助機能」を参照してください。  
  
 このトピックでは、WPF アプリケーションで動作するカスタム コントロールのサーバー側 UI オートメーション プロバイダーを実装する方法について説明します。 WPF は、ユーザー インターフェイス要素のツリーに対応するピア オートメーション オブジェクトのツリーを使用して [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] をサポートします。 テスト コードおよびユーザー補助機能を提供するアプリケーションは、オートメーション ピア オブジェクトを直接 (プロセス内コードに対して)、または [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] が提供する汎用のインターフェイスを介して使用できます。  

<a name="AutomationPeerClasses"></a>
## <a name="automation-peer-classes"></a>オートメーション ピア クラス  
 WPF コントロール[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]は、 から<xref:System.Windows.Automation.Peers.AutomationPeer>派生するピア クラスのツリーを通じてサポートされます。 規則上、ピア クラス名は、コントロールのクラス名で始まり、"AutomationPeer" で終わります。 たとえば、<xref:System.Windows.Automation.Peers.ButtonAutomationPeer><xref:System.Windows.Controls.Button>コントロール クラスのピア クラスです。 ピア クラスは[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]、コントロール型とほぼ同じですが、WPF 要素に固有です。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] インターフェイスを介して WPF アプリケーションにアクセスするオートメーション コードは、オートメーション ピアを直接使用しませんが、同じプロセス空間のオートメーション コードは、オートメーション ピアを直接使用できます。  
  
<a name="BuiltInAutomationPeerClasses"></a>
## <a name="built-in-automation-peer-classes"></a>組み込みのオートメーション ピア クラス  
 要素は、ユーザーからのインターフェイス アクティビティを受け入れる場合、またはスクリーン リーダー アプリケーションのユーザーが必要とする情報が含まれている場合、オートメーション ピア クラスを実装します。 すべての WPF のビジュアル要素にオートメーション ピアがあるわけではありません。 オートメーション ピアを実装するクラスの<xref:System.Windows.Controls.Button>例<xref:System.Windows.Controls.TextBox>としては<xref:System.Windows.Controls.Label>、 、、および が挙げられます。 オートメーション ピアを実装しないクラスの例としては、 など<xref:System.Windows.Controls.Decorator><xref:System.Windows.Controls.Border>から派生するクラスや、 や<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.Grid>に<xref:System.Windows.Controls.Canvas>基づく クラスがあります。  
  
 基本<xref:System.Windows.Controls.Control>クラスに対応するピア クラスがありません。 から<xref:System.Windows.Controls.Control>派生するカスタム コントロールに対応するピア クラスが必要な場合は、 から<xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>カスタム ピア クラスを派生させる必要があります。  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations-for-derived-peers"></a>派生ピアのセキュリティに関する考慮事項  
 オートメーション ピアは、部分信頼環境で実行する必要があります。 UIAutomationClient アセンブリ内のコードは部分信頼環境で動作するように構成されていないため、オートメーション ピア コードでそのアセンブリを参照しないでください。 代わりに、UIAutomationTypes アセンブリのクラスを使用する必要があります。 たとえば、UIAutomationTypes アセンブリ<xref:System.Windows.Automation.AutomationElementIdentifiers>のクラスを使用する<xref:System.Windows.Automation.AutomationElement>必要があります。 オートメーション ピア コードで UIAutomationTypes アセンブリを参照すると安全です。  
  
<a name="PeerNavigation"></a>
## <a name="peer-navigation"></a>ピア ナビゲーション  
 オートメーション ピアを見つけた後、インプロセス コードはオブジェクト<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A>とメソッドを呼び出すことによってピア<xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A>ツリーをナビゲートできます。 コントロール内の WPF 要素間のナビゲーションは、ピアの<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A>メソッドの実装によってサポートされます。 UI オートメーション システムは、このメソッドを呼び出して、コントロール内に含まれるサブ要素のツリーを構築します。たとえば、リスト ボックス内の項目を一覧表示します。 既定<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType>のメソッドは、要素のビジュアル ツリーを走査してオートメーション ピアのツリーを構築します。 カスタム コントロールは、このメソッドをオーバーライドして子要素をオートメーション クライアントに公開し、情報を伝達するまたはユーザーによる操作を許可する要素のオートメーション ピアを返します。  
  
<a name="Customizations"></a>
## <a name="customizations-in-a-derived-peer"></a>派生ピアのカスタマイズ  
 保護された仮想メソッド<xref:System.Windows.UIElement><xref:System.Windows.ContentElement><xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>から派生し、含まれるすべてのクラス 。 WPF<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>は、各コントロールのオートメーション ピア オブジェクトを取得する呼び出しです。 オートメーション コードは、ピアを使用して、コントロールの特性と機能に関する情報を取得し、対話型の使用をシミュレートします。 オートメーションをサポートするカスタム コントロールは<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>、 から<xref:System.Windows.Automation.Peers.AutomationPeer>派生するクラスのインスタンスをオーバーライドして返す必要があります。 たとえば、カスタム コントロールがクラスから派生する<xref:System.Windows.Controls.Primitives.ButtonBase>場合、返<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>されるオブジェクトは から<xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>派生する必要があります。  
  
 カスタム コントロールを実装する場合、カスタム コントロールに固有の動作を説明する基本オートメーション ピア クラスからの「コア」メソッドをオーバーライドする必要があります。  
  
### <a name="override-oncreateautomationpeer"></a>OnCreateAutomationPeer のオーバーライド  
 カスタム<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>コントロールのメソッドをオーバーライドして、プロバイダー オブジェクトを返します<xref:System.Windows.Automation.Peers.AutomationPeer>。  
  
### <a name="override-getpattern"></a>GetPattern のオーバーライド  
 オートメーション ピアは、サーバー側の [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] プロバイダーの実装の一部を簡略化しますが、カスタム コントロール オートメーション ピアでもパターン インターフェイスを処理する必要があります。 WPF 以外のプロバイダーと同様に、ピアは、 などの<xref:System.Windows.Automation.Provider?displayProperty=nameWithType><xref:System.Windows.Automation.Provider.IInvokeProvider>名前空間のインターフェイスの実装を提供することによってコントロール パターンをサポートします。 コントロール パターンのインターフェイスは、ピア自体または別のオブジェクトによって実装できます。 ピアの実装は、指定<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>したパターンをサポートするオブジェクトを返します。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]コードはメソッド<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>を呼び出<xref:System.Windows.Automation.Peers.PatternInterface>し、列挙値を指定します。 オーバーライド<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>は、指定されたパターンを実装するオブジェクトを返す必要があります。 コントロールにパターンのカスタム実装がない場合は、基本型の実装<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>を呼び出してその実装を取得するか、このコントロール型でパターンがサポートされていない場合は null を取得できます。 たとえば、カスタム NumericUpDown コントロールを範囲内の値に設定して、[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]ピアがインターフェイスを<xref:System.Windows.Automation.Provider.IRangeValueProvider>実装するようにできます。 次の例は、値に応答するために<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>ピアのメソッドをオーバーライドする方法を<xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>示しています。  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 メソッド<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>は、サブ要素をパターン プロバイダーとして指定することもできます。 次のコードは、<xref:System.Windows.Controls.ItemsControl>内部<xref:System.Windows.Controls.ScrollViewer>コントロールのピアにスクロール パターン処理を転送する方法を示しています。  
  
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
  
 パターン処理のサブ要素を指定するには、このコードはサブ要素オブジェクトを取得し、メソッドを使用してピア<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>を作成し、<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>新しいピアのプロパティを現在のピアに設定して、新しいピアを返します。 サブ<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>要素に設定すると、サブ要素がオートメーション ピア ツリーに表示されないようになっており、サブ要素によって発生したすべてのイベントが<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>で指定されたコントロールから発生するように指定されます。 コントロール<xref:System.Windows.Controls.ScrollViewer>はオートメーション ツリーに表示されず、生成されるスクロール イベントは<xref:System.Windows.Controls.ItemsControl>オブジェクトから発生しているように見えます。  
  
### <a name="override-core-methods"></a>「コア」メソッドのオーバーライド  
 オートメーション コードは、ピア クラスのパブリック メソッドを呼び出して、コントロールに関する情報を取得します。 コントロールに関する情報を提供するには、コントロールの実装が基本オートメーション ピア クラスで提供されているものとは異なる場合に、"Core" で終わる名前を持つ各メソッドをオーバーライドします。 コントロールは、少なくとも、<xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A>メソッドを<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>実装する必要があります。  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 の実装<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>では、値を返すことによってコントロールを<xref:System.Windows.Automation.ControlType>記述します。 を返<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>すことができますが、コントロールを正確に記述する場合は、より具体的なコントロールの種類のいずれかを返す必要があります。 戻り値の<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>場合は、プロバイダが を実装[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]するために余分[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]な作業が必要であり、クライアント製品は制御構造、キーボード操作、および可能な制御パターンを予測できません。  
  
 コントロールに<xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A>データ<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>コンテンツが含まれているか、ユーザー インターフェイス (またはその両方) で対話型ロールを果たすかを示すメソッドとメソッドを実装します。 既定では、両方のメソッドが `true` を返します。 これらの設定は、オートメーション ツリーをフィルター処理するこれらのメソッドを使用できるスクリーン リーダーなどのオートメーション ツールの使いやすさを向上します。 メソッドが<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>パターン処理をサブ要素ピアに転送する場合、サブ要素ピアの<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>メソッドは false を返して、サブ要素ピアをオートメーション ツリーから隠すことができます。 たとえば、<xref:System.Windows.Controls.ListBox>でのスクロールは<xref:System.Windows.Controls.ScrollViewer>によって処理され、 に関連付けられている<xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType>の<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>メソッド<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>によって オートメーション ピアが返されます<xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>。したがって、<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>のメソッドは<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>、`false`がオートメーション<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>ツリーに表示されないようにします。  
  
 オートメーション ピアは、コントロールに適切な既定値を提供する必要があります。 コントロールを参照する XAML は、属性を含めること<xref:System.Windows.Automation.AutomationProperties>によってコア メソッドのピア実装をオーバーライドできることに注意してください。 たとえば、次の XAML は、カスタマイズされた [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] プロパティが 2 つあるボタンを作成します。  
  
```xaml  
<Button AutomationProperties.Name="Special"
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>パターン プロバイダーの実装  
 所有する要素が<xref:System.Windows.Controls.Control>から直接派生する場合、カスタム プロバイダーによって実装されるインターフェイスは明示的に宣言されます。 たとえば、次のコードは、範囲値を実装する<xref:System.Windows.Controls.Control>ピアを宣言します。  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 所有するコントロールが、 などの<xref:System.Windows.Controls.Primitives.RangeBase>特定の種類のコントロールから派生する場合、ピアは同等の派生ピア クラスから派生できます。 この場合、ピアは<xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>から派生し、 の基本実装を提供<xref:System.Windows.Automation.Provider.IRangeValueProvider>します。 次のコードは、そのようなピアの宣言を示します。  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
実装例については、NumericUpDown カスタム コントロールを実装および使用する[C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)または[Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)のソース コードを参照してください。  
  
### <a name="raise-events"></a>イベントを発生させる  
 オートメーション クライアントは、オートメーション イベントをサブスクライブできます。 カスタム コントロールは、メソッドを呼び出すことによって<xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>、コントロールの状態に対する変更を報告する必要があります。 同様に、プロパティ値が変更された場合は<xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>、メソッドを呼び出します。 次のコードは、コントロール コード内からピア オブジェクトを取得し、イベントを発生させるメソッドを呼び出す方法を示しています。 最適化として、このコードは、このイベント型のリスナーがいるかどうかを判断します。 リスナーがいる場合にのみイベントを発生させると、不要なオーバーヘッドを回避し、コントロールの応答性を維持できます。  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションの概要](../../ui-automation/ui-automation-overview.md)
- [サーバー側 UI オートメーション プロバイダーの実装](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [ギクジットアップダウン カスタム コントロール (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [ギクジットハブのカスタム コントロール (ビジュアル ベーシック)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)

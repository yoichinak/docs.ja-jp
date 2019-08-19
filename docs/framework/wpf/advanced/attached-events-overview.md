---
title: 添付イベントの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: 40e7bd34388bec06cd8a7c3610599d814aef101f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038154"
---
# <a name="attached-events-overview"></a>添付イベントの概要

Extensible Application Markup Language (XAML) は、言語コンポーネントと、*添付イベント*と呼ばれるイベントの種類を定義します。 添付イベントという概念を利用すると、イベントを実際に定義または継承する要素にではなく、任意の要素に特定のイベントのハンドラーを追加できます。 この場合、イベントを発生させる可能性があるオブジェクトとターゲット処理インスタンスのいずれもイベントを定義せず、"所有" しません。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、「[ルーティング イベントの概要](routed-events-overview.md)」と「[XAML の概要 (WPF)](xaml-overview-wpf.md)」を既に読んでいることを前提としています。  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>添付イベントの構文  
 添付イベントには、添付イベントの使用をサポートするためにバッキングコードによって使用される必要がある XAML 構文とコーディングパターンがあります。  
  
 XAML 構文では、添付イベントはイベント名だけでなく、所有する型とイベント名をドット (.) で区切って指定されます。 イベント名はその所有タイプにより修飾されるため、添付イベントの構文では、インスタンス化できるあらゆる要素に添付イベントを添付できます。  
  
 たとえば、カスタム`NeedsCleaning`添付イベントのハンドラーをアタッチするための XAML 構文を次に示します。  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 `aqua:` 接頭辞に注意してください。この場合は、マッピングされたカスタム xmlns から来ているカスタム イベントが添付イベントであるため、この接頭辞が必要になります。  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>WPF で添付イベントを実装する方法

WPF では、添付イベントは<xref:System.Windows.RoutedEvent>フィールドによってサポートされ、発生後にツリーを通じてルーティングされます。 通常、添付イベントの発生源 (イベントを発生させたオブジェクト) はシステムまたはサービス ソースです。そのため、イベントを発生させるコードを実行するオブジェクトは要素ツリーの直接的一部ではありません。  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>添付イベントのシナリオ  
 WPF では、アタッチされたイベントは、静的<xref:System.Windows.Input.Mouse>クラス<xref:System.Windows.Controls.Validation>またはクラスによって有効にされたイベントなど、サービスレベルの抽象化が存在する特定の機能領域に存在します。 サービスと連動する、またはサービスを利用するクラスは、添付イベント構文のイベントを利用するか、クラスによるサービスの機能統合に含まれるルーティング イベントとして添付イベントを添付できます。  
  
 WPF ではアタッチされるイベントの数が定義されていますが、アタッチされたイベントを直接使用するか、処理するシナリオは非常に限られています。 通常、添付イベントはアーキテクチャの目的で機能しますが、アタッチされていない (CLR イベント "ラッパー" によってサポートされる) ルーティングイベントに転送されます。  
  
 たとえば、基になる添付イベント<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>は、XAML またはコードで添付イベントの<xref:System.Windows.UIElement.MouseDown>構文を<xref:System.Windows.UIElement>処理するのではなく、を使用して、指定さ<xref:System.Windows.UIElement>れた任意ので簡単に処理できます。 添付イベントは、入力機器の将来の拡張を可能にするため、アーキテクチャにおける目的にサービスを提供します。 仮想デバイスは、マウス入力をシミュレート<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>するためだけに発生させる必要があります。また、 <xref:System.Windows.Input.Mouse>から派生する必要はありません。 ただし、このシナリオにはイベントのコード処理が含まれ、添付イベントの XAML 処理はこのシナリオには関係ありません。  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>WPF で添付イベントを処理する  
 添付イベントと記述するハンドラー コードを処理するプロセスは基本的にルーティング イベントの場合と同じです。  
  
 一般に、WPF の添付イベントは WPF のルーティングイベントとは大きく異なります。 違いは、イベントの発生元と、クラスがメンバーとしてどのように公開されているかということです。これは、XAML ハンドラーの構文にも影響します。  
  
 ただし、前述のように、wpf のアタッチされた既存のイベントは、特に WPF での処理を目的としていません。 多くの場合、このイベントの目的は、合成中、合成された要素が親要素に状態を報告できるようにすることです。合成においては、イベントは通常、コードで発生します。また、関連する親クラスにおいて、クラスの処理に依存します。 たとえば<xref:System.Windows.Controls.Primitives.Selector> 、内の項目は添付イベントを発生させる<xref:System.Windows.Controls.Primitives.Selector.Selected>ことが想定されています。 <xref:System.Windows.Controls.Primitives.Selector>添付イベントはクラスによって<xref:System.Windows.Controls.Primitives.Selector>処理され、クラスによっ<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>て別のルーティングイベントに変換される可能性があります. ルーティング イベントとクラス処理については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>独自の添付イベントをルーティング イベントとして定義する  
 共通の WPF 基底クラスから派生する場合は、クラスに特定のパターンメソッドを組み込み、基本クラスに既に存在するユーティリティメソッドを使用して、独自のアタッチされたイベントを実装できます。  
  
 パターンは次のとおりです。  
  
- 2つのパラメーターを持つメソッドを__追加__します。 最初のパラメーターは、イベントハンドラーが追加されるインスタンスです。 2番目のパラメーターは、追加するイベントハンドラーです。 メソッドは、戻り`public`値`static`を持たないおよびである必要があります。  
  
- 2つのパラメーターを持つメソッドを__削除__します。 最初のパラメーターは、イベントハンドラーが削除されるインスタンスです。 2番目のパラメーターは、削除するイベントハンドラーです。 メソッドは、戻り`public`値`static`を持たないおよびである必要があります。  
  
 アタッチされたイベントハンドラー属性が要素で宣言されている場合、__追加の*EventName*handler__アクセサーメソッドを実行すると、XAML 処理が容易になります。 さらに、 __Add*eventname*Handler__および__Remove*eventname*ハンドラ__メソッドは、添付イベントのイベントハンドラストアへのコードアクセスを可能にします。  
  
 この一般的なパターンは、フレームワークでの実用的な実装にはまだ十分ではありません。これは、XAML リーダーの実装によって、サポートされる言語とアーキテクチャの基になるイベントを識別するためのスキームが異なる場合があるためです。 これは、WPF が添付イベントをルーティングイベントとして実装する理由の1つです。イベント (<xref:System.Windows.RoutedEvent>) に使用する識別子は、WPF イベントシステムによって既に定義されています。 また、イベントのルーティングは、添付イベントの XAML 言語レベルの概念での自然な実装拡張機能です。  
  
 WPF 添付イベントの__Add*EventName*Handler__実装は、ルーティングイベントとハンドラー <xref:System.Windows.UIElement.AddHandler%2A>を引数として使用してを呼び出すことで構成されます。  
  
 一般的に、この実装方法とルーティングイベントシステムでは、実装されて<xref:System.Windows.UIElement>いるクラスのみ<xref:System.Windows.ContentElement>が実装を持つため、添付イベント<xref:System.Windows.UIElement.AddHandler%2A>の処理が派生クラスまたは派生クラスに限定されます。  
  
 たとえば、次のコードは、添付`NeedsCleaning`イベントをルーティングイベントとし`Aquarium`て宣言する WPF 添付イベント戦略を使用して、owner クラスの添付イベントを定義します。  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 添付イベント識別子フィールド<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>を設定するために使用されるメソッドは、実際には、添付されていないルーティングイベントの登録に使用されるメソッドと同じであることに注意してください。 添付イベントとルーティング イベントはすべて、集中管理されている内部ストアに登録されます。 このイベント ストア実装により "インターフェイスとしてのイベント" という概念が可能になります。この概念に関する説明は「[ルーティング イベントの概要](routed-events-overview.md)」にあります。  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>WPF 添付イベントを発生させる  
 通常、WPF によって定義された既存の添付イベントをコードから発生させる必要はありません。 これらのイベントは、一般的な "サービス" 概念モデルに従います。 <xref:System.Windows.Input.InputManager>などのサービスクラスは、イベントの発生を担当します。  
  
 ただし、の関連付けられたイベントの WPF モデルに基づいてカスタム添付イベントを定義<xref:System.Windows.RoutedEvent>する場合は、 <xref:System.Windows.UIElement.RaiseEvent%2A>を使用して、 <xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>から添付イベントを発生させることができます。 ルーティングイベントを発生させる (アタッチまたは非表示にする) には、要素ツリー内の特定の要素をイベントソースとして宣言する必要があります。そのソースは、 <xref:System.Windows.UIElement.RaiseEvent%2A>呼び出し元として報告されます。 ツリーのソースとして報告される要素を決定することはサービスの担当です。  
  
## <a name="see-also"></a>関連項目

- [ルーティング イベントの概要](routed-events-overview.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)

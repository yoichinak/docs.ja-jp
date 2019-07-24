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
ms.openlocfilehash: a3a2f711840ad7f6e28443dac3c18501cd4400e0
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401405"
---
# <a name="attached-events-overview"></a>添付イベントの概要
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] は言語コンポーネントと*添付イベント*と呼ばれている種類のイベントを定義します。 添付イベントという概念を利用すると、イベントを実際に定義または継承する要素にではなく、任意の要素に特定のイベントのハンドラーを追加できます。 この場合、イベントを発生させる可能性があるオブジェクトとターゲット処理インスタンスのいずれもイベントを定義せず、"所有" しません。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、「[ルーティング イベントの概要](routed-events-overview.md)」と「[XAML の概要 (WPF)](xaml-overview-wpf.md)」を既に読んでいることを前提としています。  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>添付イベントの構文  
 添付イベントには [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文とコーディング パターンが含まれています。コーディング パターンは、添付イベントの使用をサポートする目的でバッキング コードで使用する必要があります。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文では、添付イベントはそのイベント名だけでなく、その所有タイプとイベント名により指定されます。所有タイプとイベント名はドット (.) で区切られます。 イベント名はその所有タイプにより修飾されるため、添付イベントの構文では、インスタンス化できるあらゆる要素に添付イベントを添付できます。  
  
 たとえば、カスタム [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 添付イベントのハンドラーを添付する `NeedsCleaning` 構文は次のようになります。  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 `aqua:` 接頭辞に注意してください。この場合は、マッピングされたカスタム xmlns から来ているカスタム イベントが添付イベントであるため、この接頭辞が必要になります。  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>WPF で添付イベントを実装する方法  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、添付イベントは<xref:System.Windows.RoutedEvent>フィールドによってサポートされ、発生後にツリーを通じてルーティングされます。 通常、添付イベントの発生源 (イベントを発生させたオブジェクト) はシステムまたはサービス ソースです。そのため、イベントを発生させるコードを実行するオブジェクトは要素ツリーの直接的一部ではありません。  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>添付イベントのシナリオ  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、アタッチされたイベントは、静的<xref:System.Windows.Input.Mouse>クラスまたは<xref:System.Windows.Controls.Validation>クラスによって有効にされたイベントなど、サービスレベルの抽象化が存在する特定の機能領域に存在します。 サービスと連動する、またはサービスを利用するクラスは、添付イベント構文のイベントを利用するか、クラスによるサービスの機能統合に含まれるルーティング イベントとして添付イベントを添付できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は添付イベントの数を定義しますが、添付イベントを直接使用または処理するシナリオは非常に限られています。 通常、添付イベントはアーキテクチャの目的で機能しますが、アタッチされていない (CLR イベント "ラッパー" によってサポートされる) ルーティングイベントに転送されます。  
  
 たとえば、またはコードで<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> <xref:System.Windows.UIElement.MouseDown> <xref:System.Windows.UIElement> <xref:System.Windows.UIElement> 添付[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]イベント構文を処理するのではなく、を使用すると、基になるアタッチされたイベントをより簡単に処理できるようになります。 添付イベントは、入力機器の将来の拡張を可能にするため、アーキテクチャにおける目的にサービスを提供します。 仮想デバイスは、マウス入力をシミュレート<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>するためだけに発生させる必要があります。また、 <xref:System.Windows.Input.Mouse>から派生する必要はありません。 ただし、このシナリオでは、イベントのコードが処理されます。添付イベントの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 処理はこのシナリオには関係しません。  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>WPF で添付イベントを処理する  
 添付イベントと記述するハンドラー コードを処理するプロセスは基本的にルーティング イベントの場合と同じです。  
  
 一般的には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベントは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ルーティング イベントとそれほど異なっているわけではありません。 違いは、イベントの発生源とメンバーとしてクラスにより公開される方法 (これは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ハンドラー構文にも影響を与えます) です。  
  
 ただし、前述のように、既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベントは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] での取り扱いを特に意図しているわけではありません。 多くの場合、このイベントの目的は、合成中、合成された要素が親要素に状態を報告できるようにすることです。合成においては、イベントは通常、コードで発生します。また、関連する親クラスにおいて、クラスの処理に依存します。 たとえば<xref:System.Windows.Controls.Primitives.Selector> 、内の項目は添付イベントを発生させる<xref:System.Windows.Controls.Primitives.Selector.Selected>ことが想定されています。 <xref:System.Windows.Controls.Primitives.Selector>添付イベントはクラスによって<xref:System.Windows.Controls.Primitives.Selector>処理され、クラスによっ<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>て別のルーティングイベントに変換される可能性があります. ルーティング イベントとクラス処理については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>独自の添付イベントをルーティング イベントとして定義する  
 共通の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基底クラスから派生させる場合、独自の添付イベントを実装できます。クラスに特定のパターン メソッドを追加し、基底クラスに既に存在するユーティリティ メソッドを使用します。  
  
 パターンは次のとおりです。  
  
- 2つのパラメーターを持つメソッドを**追加**します。 最初のパラメーターは、イベントハンドラーが追加されるインスタンスです。 2番目のパラメーターは、追加するイベントハンドラーです。 メソッドは、戻り`public`値`static`を持たないおよびである必要があります。  
  
- 2つのパラメーターを持つメソッドを**削除**します。 最初のパラメーターは、イベントハンドラーが削除されるインスタンスです。 2番目のパラメーターは、削除するイベントハンドラーです。 メソッドは、戻り`public`値`static`を持たないおよびである必要があります。  
  
 **Add*EventName*Handler**アクセサーメソッドは、アタッチ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]されたイベントハンドラー属性が要素で宣言されている場合の処理を容易にします。 さらに、 **Add*eventname*Handler**および**Remove*eventname*ハンドラ**メソッドは、添付イベントのイベントハンドラストアへのコードアクセスを可能にします。  
  
 この一般的パターンには、フレームワークの実用的実装のための十分な精度がありません。サポートする言語とアーキテクチャで基礎イベントを識別する方法に関して、特定の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リーダー実装で異なるスキームが与えられる可能性があるためです。 これは、添付イベントをルーティング[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベントとして実装する理由の1つです。イベント (<xref:System.Windows.RoutedEvent>) に使用する識別子[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、イベントシステムによって既に定義されています。 また、イベントのルーティングは、添付イベントの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 言語レベル概念で自然な実装です。  
  
 添付イベントの**Add*EventName*Handler** 実装は、ルーティングイベントとハンドラーを引数として使用してを呼び出すことで構成されます。<xref:System.Windows.UIElement.AddHandler%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 一般的に、この実装方法とルーティングイベントシステムでは、実装されて<xref:System.Windows.UIElement>いるクラスのみ<xref:System.Windows.ContentElement>が実装を持つため、添付イベント<xref:System.Windows.UIElement.AddHandler%2A>の処理が派生クラスまたは派生クラスに限定されます。  
  
 たとえば、次のコードは、添付イベントをルーティング イベントとして宣言する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベント方法を利用し、所有者クラス `Aquarium` で `NeedsCleaning` 添付イベントを定義します。  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 添付イベント識別子フィールド<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>を設定するために使用されるメソッドは、実際には、添付されていないルーティングイベントの登録に使用されるメソッドと同じであることに注意してください。 添付イベントとルーティング イベントはすべて、集中管理されている内部ストアに登録されます。 このイベント ストア実装により "インターフェイスとしてのイベント" という概念が可能になります。この概念に関する説明は「[ルーティング イベントの概要](routed-events-overview.md)」にあります。  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>WPF 添付イベントを発生させる  
 通常、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義の既存の添付イベントはコードから発生させる必要がありません。 これらのイベントは、一般的な "サービス" 概念モデルに従います。 <xref:System.Windows.Input.InputManager>などのサービスクラスは、イベントの発生を担当します。  
  
 ただし、の関連付けられたイベント[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のモデルに基づいてカスタム添付イベントを定義する場合は、を使用<xref:System.Windows.UIElement.RaiseEvent%2A>して<xref:System.Windows.RoutedEvent>、 <xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>から添付イベントを発生させることができます。 ルーティングイベントを発生させる (アタッチまたは非表示にする) には、要素ツリー内の特定の要素をイベントソースとして宣言する必要があります。そのソースは、 <xref:System.Windows.UIElement.RaiseEvent%2A>呼び出し元として報告されます。 ツリーのソースとして報告される要素を決定することはサービスの担当です。  
  
## <a name="see-also"></a>関連項目

- [ルーティング イベントの概要](routed-events-overview.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)

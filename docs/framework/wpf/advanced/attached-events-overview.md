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
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141563"
---
# <a name="attached-events-overview"></a>添付イベントの概要

拡張可能なアプリケーション マークアップ言語 (XAML) では *、"添付イベント*" と呼ばれる言語コンポーネントとイベントの種類を定義します。 添付イベントという概念を利用すると、イベントを実際に定義または継承する要素にではなく、任意の要素に特定のイベントのハンドラーを追加できます。 この場合、イベントを発生させる可能性があるオブジェクトとターゲット処理インスタンスのいずれもイベントを定義せず、"所有" しません。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、「[ルーティング イベントの概要](routed-events-overview.md)」と「[XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)」を既に読んでいることを前提としています。  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>添付イベントの構文  
 添付イベントには XAML 構文とコーディング パターンがあり、添付イベントの使用をサポートするためにバッキング コードで使用する必要があります。  
  
 XAML 構文では、添付イベントは、イベント名だけでなく、所有する型とイベント名をドット (.) で区切って指定します。 イベント名はその所有タイプにより修飾されるため、添付イベントの構文では、インスタンス化できるあらゆる要素に添付イベントを添付できます。  
  
 たとえば、カスタム`NeedsCleaning`添付イベントのハンドラーをアタッチするための XAML 構文を次に示します。  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 `aqua:` 接頭辞に注意してください。この場合は、マッピングされたカスタム xmlns から来ているカスタム イベントが添付イベントであるため、この接頭辞が必要になります。  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>WPF で添付イベントを実装する方法

WPF では、アタッチされたイベントは<xref:System.Windows.RoutedEvent>フィールドによってバックアップされ、発生後にツリーを通じてルーティングされます。 通常、添付イベントの発生源 (イベントを発生させたオブジェクト) はシステムまたはサービス ソースです。そのため、イベントを発生させるコードを実行するオブジェクトは要素ツリーの直接的一部ではありません。  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>添付イベントのシナリオ  
 WPF では、静的<xref:System.Windows.Input.Mouse>クラスやクラスによって有効になるイベントなど、サービス レベルの抽象化がある特定の機能領域に添付イベントが存在します。 <xref:System.Windows.Controls.Validation> サービスと連動する、またはサービスを利用するクラスは、添付イベント構文のイベントを利用するか、クラスによるサービスの機能統合に含まれるルーティング イベントとして添付イベントを添付できます。  
  
 WPF では、添付イベントの数を定義しますが、アタッチされたイベントを直接使用または処理するシナリオは非常に限られています。 一般に、アタッチされたイベントはアーキテクチャの目的で使用されますが、その後、(CLR イベント "ラッパー" を使用してサポートされる) 非添付イベントに転送されます。  
  
 たとえば、XAML またはコードで<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>添付イベント構文を処理<xref:System.Windows.UIElement><xref:System.Windows.UIElement.MouseDown><xref:System.Windows.UIElement>するのではなく、そのイベントで使用することで、基になる添付イベントをより簡単に処理できます。 添付イベントは、入力機器の将来の拡張を可能にするため、アーキテクチャにおける目的にサービスを提供します。 架空のデバイスは、マウス入力をシミュレートするために発生<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>させるだけで、それを派生<xref:System.Windows.Input.Mouse>させる必要はありません。 ただし、このシナリオでは、イベントのコード処理が含まれますが、アタッチされたイベントの XAML 処理はこのシナリオには関係ありません。  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>WPF で添付イベントを処理する  
 添付イベントと記述するハンドラー コードを処理するプロセスは基本的にルーティング イベントの場合と同じです。  
  
 一般に、WPF 添付イベントは WPF ルーティング イベントとあまり変わりません。 違いは、イベントのソースの方法と、イベントがメンバーとしてクラスによって公開される方法です (XAML ハンドラー構文にも影響します)。  
  
 ただし、前述したように、既存の WPF 添付イベントは特に WPF での処理を目的としていません。 多くの場合、このイベントの目的は、合成中、合成された要素が親要素に状態を報告できるようにすることです。合成においては、イベントは通常、コードで発生します。また、関連する親クラスにおいて、クラスの処理に依存します。 たとえば、<xref:System.Windows.Controls.Primitives.Selector>内の項目は、アタッチされた<xref:System.Windows.Controls.Primitives.Selector.Selected>イベントを発生させると想定され、クラスによって<xref:System.Windows.Controls.Primitives.Selector>クラスが処理され、クラスによって別<xref:System.Windows.Controls.Primitives.Selector>のルーティング イベントに変換される<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>可能性があります。 ルーティング イベントとクラス処理については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>独自の添付イベントをルーティング イベントとして定義する  
 共通 WPF 基本クラスから派生している場合は、クラスに特定のパターン メソッドを含め、基底クラスに既に存在するユーティリティ メソッドを使用して、独自の添付イベントを実装できます。  
  
 パターンは次のとおりです。  
  
- 2 つのパラメーターを持つ__*メソッド追加イベント名*ハンドラー__ 。 最初のパラメーターは、イベント ハンドラーが追加されるインスタンスです。 2 番目のパラメーターは、追加するイベント ハンドラーです。 メソッドは、`public`および`static`に戻り値を指定する必要があります。  
  
- 2 つのパラメーターを持つ__*メソッドのイベント名*ハンドラーを削除__します。 最初のパラメーターは、イベント ハンドラーが削除されるインスタンスです。 2 番目のパラメーターは、削除するイベント ハンドラーです。 メソッドは、`public`および`static`に戻り値を指定する必要があります。  
  
 __Add*EventName*ハンドラー__アクセサー メソッドは、添付イベント ハンドラー属性が要素で宣言されたときに XAML 処理を容易にします。 イベント__*名*ハンドラーの追加__と__イベント*名*ハンドラーの削除メソッド__を使用すると、アタッチされたイベントのイベント ハンドラー ストアへのコード アクセスも有効になります。  
  
 この一般的なパターンは、サポート言語とアーキテクチャで基になるイベントを識別するための異なるスキームを持つ場合があるため、フレームワークでの実用的な実装に十分な正確さではありません。 これは、WPF が添付イベントをルーティング イベントとして実装する理由の 1 つです。イベント ( )<xref:System.Windows.RoutedEvent>に使用する識別子は、WPF イベント システムによって既に定義されています。 また、イベントのルーティングは、添付イベントの XAML 言語レベルの概念に対する自然な実装拡張です。  
  
 WPF 添付__イベントの*イベント名*ハンドラーの追加__実装は、ルーティング<xref:System.Windows.UIElement.AddHandler%2A>イベントとハンドラーを引数として呼び出すで構成されます。  
  
 この実装戦略とルーティング イベント システムは、一般に、<xref:System.Windows.UIElement><xref:System.Windows.ContentElement><xref:System.Windows.UIElement.AddHandler%2A>派生クラスまたは派生クラスへの添付イベントの処理を制限します。  
  
 たとえば、次のコードでは、添付`NeedsCleaning`イベントをルーティング イベントとして`Aquarium`宣言する WPF 添付イベント戦略を使用して、owner クラス で添付イベントを定義します。  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 添付イベント識別子フィールド の を確立するために使用されるメソッド<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>は、実際には、アタッチされていないルーティング イベントを登録するために使用されるメソッドと同じです。 添付イベントとルーティング イベントはすべて、集中管理されている内部ストアに登録されます。 このイベント ストア実装により "インターフェイスとしてのイベント" という概念が可能になります。この概念に関する説明は「[ルーティング イベントの概要](routed-events-overview.md)」にあります。  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>WPF 添付イベントを発生させる  
 通常、WPF で定義された既存の添付イベントをコードから発生させる必要はありません。 これらのイベントは、一般的な "サービス" 概念モデルに<xref:System.Windows.Input.InputManager>従い、イベントの発生を担当するなどのサービス クラスが実行されます。  
  
 <xref:System.Windows.RoutedEvent>ただし、WPF の添付イベント モデルに基づいてカスタム添付イベントを定義する場合は、<xref:System.Windows.UIElement.RaiseEvent%2A><xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>から添付イベントを発生させることができます。 ルーティング イベントを発生させる (アタッチされているかどうかにかかわらず) には、要素ツリー内の特定の要素をイベント ソースとして宣言する必要があります。そのソースは呼び出<xref:System.Windows.UIElement.RaiseEvent%2A>し元として報告されます。 ツリーのソースとして報告される要素を決定することはサービスの担当です。  
  
## <a name="see-also"></a>関連項目

- [ルーティング イベントの概要](routed-events-overview.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)

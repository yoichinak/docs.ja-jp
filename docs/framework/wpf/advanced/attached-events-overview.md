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
ms.openlocfilehash: 8586f09d5c12f732c63bccf4682edf94144fd47f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371672"
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
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、添付イベントが支え、<xref:System.Windows.RoutedEvent>フィールドおよび発生後に、ツリーを介してルーティングされます。 通常、添付イベントの発生源 (イベントを発生させたオブジェクト) はシステムまたはサービス ソースです。そのため、イベントを発生させるコードを実行するオブジェクトは要素ツリーの直接的一部ではありません。  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>添付イベントのシナリオ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、添付イベントは、特定の機能領域に存在する、静的で有効になっているイベントのサービス レベルの抽象化などが<xref:System.Windows.Input.Mouse>クラスまたは<xref:System.Windows.Controls.Validation>クラス。 サービスと連動する、またはサービスを利用するクラスは、添付イベント構文のイベントを利用するか、クラスによるサービスの機能統合に含まれるルーティング イベントとして添付イベントを添付できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は添付イベントの数を定義しますが、添付イベントを直接使用または処理するシナリオは非常に限られています。 一般的には、添付イベントはアーキテクチャ目的にサービスを提供しますが、その後、非添付の ([!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベント "ラッパー" でサポートされる) ルーティング イベントに転送されます。  
  
 たとえば、基になる添付イベント<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>より簡単に処理できる、特定の<xref:System.Windows.UIElement>を使用して<xref:System.Windows.UIElement.MouseDown>を<xref:System.Windows.UIElement>か、添付イベント構文を処理するのではなくで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]またはコード。 添付イベントは、入力機器の将来の拡張を可能にするため、アーキテクチャにおける目的にサービスを提供します。 させる仮定のデバイスのみ必要があります<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>で、マウスの入力をシミュレートするために順序付けおよびから派生する必要はありません<xref:System.Windows.Input.Mouse>するようにします。 ただし、このシナリオでは、イベントのコードが処理されます。添付イベントの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 処理はこのシナリオには関係しません。  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>WPF で添付イベントを処理する  
 添付イベントと記述するハンドラー コードを処理するプロセスは基本的にルーティング イベントの場合と同じです。  
  
 一般的には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベントは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ルーティング イベントとそれほど異なっているわけではありません。 違いは、イベントの発生源とメンバーとしてクラスにより公開される方法 (これは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ハンドラー構文にも影響を与えます) です。  
  
 ただし、前述のように、既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベントは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] での取り扱いを特に意図しているわけではありません。 多くの場合、このイベントの目的は、合成中、合成された要素が親要素に状態を報告できるようにすることです。合成においては、イベントは通常、コードで発生します。また、関連する親クラスにおいて、クラスの処理に依存します。 内のアイテムなど、 <xref:System.Windows.Controls.Primitives.Selector> 、添付を生成する必要があります<xref:System.Windows.Controls.Primitives.Selector.Selected>によって、クラスでは、そのイベントが処理される、<xref:System.Windows.Controls.Primitives.Selector>クラスし、で可能性のある変換、<xref:System.Windows.Controls.Primitives.Selector>クラス別のルーティング イベントを<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. ルーティング イベントとクラス処理については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>独自の添付イベントをルーティング イベントとして定義する  
 共通の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基底クラスから派生させる場合、独自の添付イベントを実装できます。クラスに特定のパターン メソッドを追加し、基底クラスに既に存在するユーティリティ メソッドを使用します。  
  
 パターンは次のとおりです。  
  
-   メソッド**追加*EventName*ハンドラー** 2 つのパラメーターを使用します。 最初のパラメーターは、イベントを識別して、特定のイベントを持つ名前が一致する必要があります、 ***EventName***メソッド名。 2 番目のパラメーターは追加するハンドラーです。 メソッドである必要があります`public`と`static`、戻り値はありません。  
  
-   メソッド**削除*EventName*ハンドラー** 2 つのパラメーターを使用します。 最初のパラメーターは、イベントを識別して、特定のイベントを持つ名前が一致する必要があります、 ***EventName***メソッド名。 2 番目のパラメーターは削除するハンドラーです。 メソッドである必要があります`public`と`static`、戻り値はありません。  
  
 **追加*EventName*ハンドラー**アクセサー メソッドを容易に、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性が要素で宣言されたイベント ハンドラーをアタッチするときに処理します。 **追加*EventName*ハンドラー**と**削除*EventName*ハンドラー**メソッドでは、コードのイベント ハンドラー ストアへのアクセスも有効にします添付イベント。  
  
 この一般的パターンには、フレームワークの実用的実装のための十分な精度がありません。サポートする言語とアーキテクチャで基礎イベントを識別する方法に関して、特定の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リーダー実装で異なるスキームが与えられる可能性があるためです。 これは、理由の 1 つを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ルーティング イベントとして実装がアタッチされているイベントはイベントを使用する識別子 (<xref:System.Windows.RoutedEvent>) で定義されている、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント システム。 また、イベントのルーティングは、添付イベントの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 言語レベル概念で自然な実装です。  
  
 **追加*EventName*ハンドラー**の実装を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]添付イベントの呼び出し元の構成、<xref:System.Windows.UIElement.AddHandler%2A>ルーティング イベントとハンドラーの引数として使用します。  
  
 この実装方法と、ルーティング イベント システム制限するか、添付イベントの処理が一般に<xref:System.Windows.UIElement>派生クラスまたは<xref:System.Windows.ContentElement>クラスだけであるため、クラスを派生<xref:System.Windows.UIElement.AddHandler%2A>実装します。  
  
 たとえば、次のコードは、添付イベントをルーティング イベントとして宣言する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベント方法を利用し、所有者クラス `Aquarium` で `NeedsCleaning` 添付イベントを定義します。  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 添付イベント id フィールドを確立するために、メソッドを使用することに注意してください。 <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>、実際にメソッドと同じ非添付のルーティング イベントを登録するために使用します。 添付イベントとルーティング イベントはすべて、集中管理されている内部ストアに登録されます。 このイベント ストア実装により "インターフェイスとしてのイベント" という概念が可能になります。この概念に関する説明は「[ルーティング イベントの概要](routed-events-overview.md)」にあります。  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>WPF 添付イベントを発生させる  
 通常、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義の既存の添付イベントはコードから発生させる必要がありません。 これらのイベントを選択し、一般的な「サービス」概念モデルに従い、サービス クラスなど<xref:System.Windows.Input.InputManager>イベントの生成を担当します。  
  
 ただし、に基づいてカスタム添付イベントを定義するかどうか、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ベースのモデルでイベントをアタッチする<xref:System.Windows.RoutedEvent>、使用することができます<xref:System.Windows.UIElement.RaiseEvent%2A>いずれかから添付イベントを発生させる<xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>します。 (添付または非) ルーティング イベントを発生させるには、イベント ソースとして要素ツリー内の特定の要素を宣言することが必要です。そのソースとして報告、<xref:System.Windows.UIElement.RaiseEvent%2A>呼び出し元。 ツリーのソースとして報告される要素を決定することはサービスの担当です。  
  
## <a name="see-also"></a>関連項目
- [ルーティング イベントの概要](routed-events-overview.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)

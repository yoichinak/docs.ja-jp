---
title: 弱いイベント パターン
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: e0cd6837de626fa6bcd560811c6a70f7f6604daa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316168"
---
# <a name="weak-event-patterns"></a>弱いイベント パターン
アプリケーションでは、イベント ソースに接続されているハンドラーがハンドラーをソースに接続されているリスナーのオブジェクトと連携して破棄されないです。 このような状況は、メモリ リークにつながります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 特定のイベントの専任マネージャー クラスを提供することでそのイベントのリスナー インターフェイスを実装してこの問題に対処するために使用する設計パターンについて説明します。 この設計パターンと呼ばれる、*弱いイベント パターン*します。  
  
## <a name="why-implement-the-weak-event-pattern"></a>弱いイベント パターンを実装する理由  
 イベントのリッスンは、メモリ リークにつながります。 イベントをリッスンするための一般的な手法では、ソースでのイベントにハンドラーをアタッチする言語固有の構文を使用します。 たとえば、 C#、構文がある:`source.SomeEvent += new SomeEventHandler(MyEventHandler)`します。  
  
 この手法は、イベント リスナーをイベント ソースからの強い参照を作成します。 通常、リスナーのイベント ハンドラーをアタッチするオブジェクトの有効期間は、ソースのオブジェクトの有効期間によって影響を受ける (ない場合、イベント ハンドラーが明示的に削除) を使用するリスナーと、します。 ただし、特定の状況で、ソースの有効期間ではなく、アプリケーションのビジュアル ツリーに現在属しているかどうかなど、他の要因によって制御するリスナーのオブジェクトの有効期間をする可能性があります。 ソース オブジェクトの有効期間が、リスナーのオブジェクトの有効期間を超えるたびに通常のイベント パターンにより、メモリ リーク。 リスナーは長い時間動作させるためのものよりもします。  
  
 弱いイベント パターンは、このメモリ リークの問題を解決するために設計されています。 リスナーは、イベントに登録する必要がありますが、リスナーは明示的に認識されませんの登録を解除するたびに、弱いイベント パターンを使用できます。 弱いイベント パターンは、ソースのオブジェクトの有効期間は、リスナーの役に立つオブジェクトの有効期間を超えた場合にも使用できます。 (この場合、*便利な*するによって決定されます)。弱いイベント パターンは、リスナーを登録し、任意の方法でリスナーのオブジェクトの有効期間の特性に影響を与えずに、イベントを受信できます。 実際には、ソースからの暗黙的な参照では、リスナーは、ガベージ コレクションの対象かどうかは不明です。 参照が弱いイベント パターンと、関連の名前付けため、弱い参照[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]します。 リスナーはガベージ収集または破棄されるそれ以外の場合、ソースが破棄されたオブジェクトへの要素も形成ハンドラーの参照を保持せずに続行できます。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>弱いイベント パターンを実装する必要がありますか。  
 弱いイベント パターンの実装は、主にコントロールの作成者にとって重要です。 コントロールの作成者は、動作と、コントロールとを挿入するアプリケーションに与える影響を抑制担当大きくします。 これが含まれています、コントロール オブジェクトの有効期間動作には具体的に説明されているメモリ リークの問題の処理には。  
  
 特定のシナリオでは、弱いイベント パターンのアプリケーションに自体本質的に役立ちます。 このような 1 つのシナリオは、データ バインディングです。 データ バインディングでは、バインディングのターゲットとなるリスナー オブジェクトの完全に独立したソース オブジェクトの一般的なは。 さまざまな側面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]弱いイベント パターン、イベントの実装方法に適用されるバインディングが既にデータがあります。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>弱いイベント パターンを実装する方法  
 弱いイベント パターンを実装する次の 3 つの方法はあります。 次の表は、3 つの方法を示し、それぞれを使用する際のガイダンスを提供します。  
  
|方法|いつ実装するには|  
|--------------|-----------------------|  
|既存の弱いイベント マネージャー クラスを使用して、|サブスクライブするイベントに対応する場合<xref:System.Windows.WeakEventManager>、既存の弱いイベント マネージャーを使用します。 WPF に含まれている弱いイベント マネージャーの一覧での継承階層を参照してください、<xref:System.Windows.WeakEventManager>クラス。 弱いイベントが含まれるマネージャーは、制限付きであるために、他の方法のいずれかを選択する必要があります。|  
|ジェネリックの弱いイベント マネージャー クラスを使用します。|ジェネリックを使用して、<xref:System.Windows.WeakEventManager%602>既存<xref:System.Windows.WeakEventManager>効率性について利用できないを実装する簡単な方法を必要し、していない懸念しています。 ジェネリック<xref:System.Windows.WeakEventManager%602>既存またはカスタムの弱いイベント マネージャーより非効率です。 たとえば、ジェネリック クラスは、discover イベントのイベントの名前を指定するために複数のリフレクションが。 ジェネリックを使用して、イベントを登録するコードも、<xref:System.Windows.WeakEventManager%602>より既存を使用するよりも詳細またはカスタム<xref:System.Windows.WeakEventManager>します。|  
|カスタムの弱いイベント マネージャー クラスを作成します。|カスタムを作成する<xref:System.Windows.WeakEventManager>既存<xref:System.Windows.WeakEventManager>をご利用いただけません最適な効率性を必要とします。 カスタムを使用して<xref:System.Windows.WeakEventManager>をサブスクライブするイベントをより効率的になりますが、先頭に複数のコードを作成するコストが発生する操作を行います。|  
|サード パーティ製の弱いイベント マネージャーを使用します。|NuGet が[いくつかの弱いイベント マネージャー](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)と WPF の多くのフレームワークは、パターンもサポート (たとえばを参照してください[疎結合イベント サブスクリプションの Prism のドキュメント](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events))。|

 次のセクションでは、弱いイベント パターンを実装する方法について説明します。  この説明のためは、サブスクライブするイベントは、次の特性を持ちます。  
  
-   イベントの名前は`SomeEvent`します。  
  
-   イベントが発生した、`EventSource`クラス。  
  
-   イベント ハンドラーが型: `SomeEventEventHandler` (または`EventHandler<SomeEventEventArgs>`)。  
  
-   このイベントは、型のパラメーターを渡します`SomeEventEventArgs`イベント ハンドラーにします。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>既存の弱いイベント マネージャー クラスを使用します。  
  
1. 既存の弱いイベント マネージャーを検索します。  
  
     WPF に含まれている弱いイベント マネージャーの一覧での継承階層を参照してください、<xref:System.Windows.WeakEventManager>クラス。  
  
2. 通常のイベント フックアップではなく、新しい弱いイベント マネージャーを使用します。  
  
     たとえば、コードでは、次のパターンを使用して、イベントにサブスクライブするとします。  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様に、コードでは、次のパターンを使用して、イベント サブスクリプションを解除する場合。  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>ジェネリックの弱いイベント マネージャー クラスを使用します。  
  
1. ジェネリックを使用して、<xref:System.Windows.WeakEventManager%602>通常のイベント フックアップではなくクラス。  
  
     使用すると<xref:System.Windows.WeakEventManager%602>イベント リスナーを登録するには、イベント ソースを指定し、<xref:System.EventArgs>クラスと呼び出しに型パラメーターとして型<xref:System.Windows.WeakEventManager%602.AddHandler%2A>次のコードに示すように。  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>カスタムの弱いイベント マネージャー クラスを作成します。  
  
1. 次のクラス テンプレートをプロジェクトにコピーします。  
  
     このクラスから継承、<xref:System.Windows.WeakEventManager>クラス。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. 置換、`SomeEventWeakEventManager`名に置き換えて名前。  
  
3. 前に、イベントの名前と説明した 3 つの名前に置き換えます。 (`SomeEvent`、 `EventSource`、および`SomeEventEventArgs`)  
  
4. 管理イベントと同様に表示するには、弱いイベント マネージャー クラスの可視性 (パブリック/内部/プライベート) を設定します。  
  
5. 通常のイベント フックアップではなく、新しい弱いイベント マネージャーを使用します。  
  
     たとえば、コードでは、次のパターンを使用して、イベントにサブスクライブするとします。  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様に、コードは、イベントをアンサブスク ライブする次のパターンを使用する場合。  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [ルーティング イベントの概要](routed-events-overview.md)
- [データ バインディングの概要](../data/data-binding-overview.md)

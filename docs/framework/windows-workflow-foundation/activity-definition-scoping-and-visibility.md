---
title: アクティビティ定義のスコープ設定と表示
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: 27c43323a176c841f3d90cb9c52f25599bc0686d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325216"
---
# <a name="activity-definition-scoping-and-visibility"></a>アクティビティ定義のスコープ設定と表示
アクティビティ定義のスコープと可視性は、オブジェクトのスコープと可視性と同様に、他のオブジェクトまたはアクティビティがアクティビティのメンバーにアクセスするために必要な機能です。 アクティビティ定義は次の実装によって実行されます。  
  
1. アクティビティによってユーザーに公開されるメンバー (<xref:System.Activities.Argument>、<xref:System.Activities.Variable>、および <xref:System.Activities.ActivityDelegate> オブジェクト、および子アクティビティ) の指定。  
  
2. アクティビティの実行ロジックの実装。  
  
 この実装には、アクティビティのコンシューマーには公開されないが、実装の詳細であるメンバーが含まれる場合があります。  型定義と同様に、作成者は、アクティビティ モデルを使用することで、定義対象のアクティビティの定義について、アクティビティ メンバーの可視性を指定できます。  この可視性によって、データのスコープなどメンバーの使用法の要素が決定します。  
  
## <a name="scope"></a>スコープ  
 データのスコープ以外に、アクティビティ モデルの可視性によって、検証、デバッグ、追跡、トレースなどのアクティビティの他の要素へのアクセスが制限される場合があります。 実行プロパティでは、実行の特性を特定の定義のスコープに制限するための可視性とスコープを使用します。 セカンダリ ルートでは、可視性とスコープを使用して、<xref:System.Activities.Statements.CompensableActivity> によってキャプチャされた状態を補正可能なアクティビティが使用される定義のスコープに制限します。  
  
## <a name="definition-and-usage"></a>定義と使用法  
 ワークフローは、基本アクティビティ クラスから継承することによってからのアクティビティを使用して新しいアクティビティの作成によって書き込まれて、[ビルトイン アクティビティ ライブラリ](net-framework-4-5-built-in-activity-library.md)します。 アクティビティを使用するには、アクティビティ作成者によってその定義の各コンポーネントの可視性が設定される必要があります。  
  
### <a name="activity-members"></a>アクティビティ メンバー  
 アクティビティ モデルでは、アクティビティによってコンシューマーが使用できるようになる引数、変数、デリゲート、および子アクティビティが定義されます。 各メンバーは、`public` または `private` として宣言できます。 パブリック メンバーはアクティビティのコンシューマーが設定し、`private` メンバーはアクティビティの作成者によって指定された実装を使用します。 データのスコープの可視性に関する規則は、次のとおりです。  
  
1. パブリック メンバーおよびパブリック子アクティビティのパブリック メンバーは、パブリック変数を参照できます。  
  
2. プライベート メンバーおよびパブリック子アクティビティのパブリック メンバーは引数およびプライベート変数を参照できます。  
  
 アクティビティのコンシューマーが設定可能なメンバーは、プライベートに指定できません。  
  
### <a name="authoring-models"></a>作成モデル  
 カスタム アクティビティは、<xref:System.Activities.NativeActivity>、<xref:System.Activities.Activity>、<xref:System.Activities.CodeActivity>、または <xref:System.Activities.AsyncCodeActivity> を使用して定義されます。 これらのクラスから派生するアクティビティによって、可視性が異なるさまざまなメンバー型が公開されます。  
  
#### <a name="nativeactivity"></a>NativeActivity  
 <xref:System.Activities.NativeActivity> から派生したアクティビティの動作は、命令型コードで記述され、任意で既存のアクティビティを使用して定義できます。 <xref:System.Activities.NativeActivity> からアクティビティを派生させると、ランタイムによって公開されるすべての機能にアクセスできます。 このようなアクティビティのメンバーは、引数を除く `public` としてのみ宣言可能なパブリックまたはプライベートの可視性を使用して定義できます。  
  
 <xref:System.Activities.NativeActivity> から派生したクラスのメンバーは、<xref:System.Activities.NativeActivityMetadata> メソッドに渡される <xref:System.Activities.NativeActivity.CacheMetadata%2A> 構造体を使用してランタイムに宣言されます。  
  
#### <a name="activity"></a>アクティビティ  
 <xref:System.Activities.Activity> を使用して作成されたアクティビティの動作は、他のアクティビティが作成されることで厳密にデザインされます。 <xref:System.Activities.Activity> クラスの 1 つの実装子アクティビティは、<xref:System.Activities.Activity.Implementation%2A> を使用するランタイムによって取得されます。 <xref:System.Activities.Activity> から派生するアクティビティは、パブリック引数、パブリック変数、インポートされた ActivityDelegates、およびインポートされた Activities を定義します。  
  
 インポートされた ActivityDelegates および Activities は、パブリックのアクティビティの子として宣言されますが、アクティビティによって直接はスケジュールされません。 この情報は検証時に使用され、アクティビティが実行されないロケーションで複数の親が同時に検証されるのを防ぎます。 また、パブリック子と同様に、インポートされた子は、アクティビティの実装時に参照およびスケジュールされます。 つまり、Activity1 と呼ばれるアクティビティをインポートするアクティビティには、Activity1 をスケジュールする実装の <xref:System.Activities.Statements.Sequence> が含まれている場合があります。  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity/ AsyncCodeActivity  
 この基本クラスは、命令型コードの動作の定義に使用されます。 このクラスから派生したアクティビティだけが、このアクティビティよって公開された引数にアクセスできます。 つまり、これらのアクティビティによって公開されるメンバーのみがパブリック引数になります。 他のメンバーおよび可視性はこれらのアクティビティに適用されません。  
  
#### <a name="summary-of-visibilities"></a>可視性の概要  
 このセクションの前半の情報の概要を次の表に示します。  
  
|メンバーの型|NativeActivity|アクティビティ|CodeActivity/ AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|引数|パブリック/プライベート|Public|該当なし|  
|変数|パブリック/プライベート|Public|該当なし|  
|Child Activities|パブリック/プライベート|パブリック (実装時に定義された修正済みのプライベート子)|該当なし|  
|ActivityDelegates|パブリック/プライベート|Public|該当なし|  
  
 通常、アクティビティのコンシューマーが設定不可能なメンバーは、パブリックに指定できません。  
  
### <a name="execution-properties"></a>実行プロパティ  
 状況によっては、特定の実行プロパティのスコープをアクティビティのパブリック子に限定すると便利な場合があります。 <xref:System.Activities.ExecutionProperties> コレクションによって、<xref:System.Activities.ExecutionProperties.Add%2A> メソッドでこれを実行できます。 このメソッドの Boolean 型パラメーターは、特定のプロパティのスコープがすべての子に限定されているか、パブリックである子にのみ限定されているかを示します。 このパラメーターが `true` に設定されている場合、プロパティはパブリック メンバーおよびパブリック子のパブリック メンバーに可視性が限定されます。  
  
### <a name="secondary-roots"></a>セカンダリ ルート  
 セカンダリ ルートは、補正アクティビティの状態を管理するためのランタイムの内部の機構です。 <xref:System.Activities.Statements.CompensableActivity> の実行が終了しても、その状態はすぐにクリーン アップされません。 代わりに、補正が完了するまで、セカンダリ ルートのランタイムによってこの状態が維持されます。 セカンダリ ルートによってキャプチャされた配置環境は、補正可能なアクティビティが使用される定義のスコープに対応します。

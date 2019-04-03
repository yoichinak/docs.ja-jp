---
title: WF 内での非同期アクティビティの作成
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: 5d8659ee57f9bb576cd7066652a294717811432f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712275"
---
# <a name="creating-asynchronous-activities-in-wf"></a>WF 内での非同期アクティビティの作成
<xref:System.Activities.AsyncCodeActivity> は使用する基本クラスをアクティビティ作成者に提供します。その結果、派生アクティビティが非同期実行ロジックを実装できるようになります。 これは、ワークフローのスケジューラ スレッドを保持したり、並行して実行される可能性があるすべてのアクティビティをブロックしたりすることなく、非同期作業を実行する必要があるカスタム アクティビティに役立ちます。 ここでは、<xref:System.Activities.AsyncCodeActivity> を使用してカスタムの非同期アクティビティを作成する方法の概要を説明します。  
  
## <a name="using-asynccodeactivity"></a>AsyncCodeActivity の使用  
 <xref:System.Activities?displayProperty=nameWithType> は、カスタム アクティビティ作成者に、アクティビティの作成要件に応じてさまざまな基本クラスを提供します。 それぞれが特定のセマンティックを持ち、ワークフロー作成者 (およびアクティビティ ランタイム) に対応するコントラクトを提供します。 <xref:System.Activities.AsyncCodeActivity> ベースのアクティビティは、スケジューラ スレッド、およびマネージド コードで表される実行ロジックに関連して、非同期に作業を実行するアクティビティです。 非同期作業になると、<xref:System.Activities.AsyncCodeActivity> によって実行中にアイドル ポイントが発生する可能性があります。 非同期作業には揮発的な性質があるため、<xref:System.Activities.AsyncCodeActivity> はアクティビティの実行期間に対して常に非永続的なブロックを作成します。 こうすることで、ワークフロー ランタイムによって、非同期作業中にワークフロー インスタンスが永続化されることを回避できます。また、非同期コードの実行中にワークフロー インスタンスがアンロードされることを回避できます。  
  
### <a name="asynccodeactivity-methods"></a>AsyncCodeActivity メソッド  
 <xref:System.Activities.AsyncCodeActivity> から派生するアクティビティでは、<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> メソッドと <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> メソッドをカスタム コードでオーバーライドすることで、非同期実行ロジックを作成できます。 ランタイムによって呼び出されるとき、これらのメソッドには <xref:System.Activities.AsyncCodeActivityContext> が渡されます。 <xref:System.Activities.AsyncCodeActivityContext> により、アクティビティ作成者はにわたる共有状態を提供する<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>のコンテキスト内<xref:System.Activities.AsyncCodeActivityContext.UserState%2A>プロパティ。 次の例では、`GenerateRandom` アクティビティによって非同期に乱数を生成します。  
  
 [!code-csharp[CFX_ActivityExample#8](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 前の例のアクティビティは、<xref:System.Activities.AsyncCodeActivity%601> から派生し、`OutArgument<int>` という昇格した `Result` を備えています。 `GetRandom` メソッドが返す値は、<xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> のオーバーライドによって抽出され、返されます。また、この値は `Result` 値として設定されます。 結果を返さない非同期アクティビティは、<xref:System.Activities.AsyncCodeActivity> から派生する必要があります。 次の例では、`DisplayRandom` から派生する <xref:System.Activities.AsyncCodeActivity> アクティビティが定義されます。 このアクティビティは `GetRandom` アクティビティに似ていますが、結果を返す代わりにコンソールにメッセージを表示します。  
  
 [!code-csharp[CFX_ActivityExample#11](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 戻り値がないため、`DisplayRandom` は <xref:System.Action> の代わりに <xref:System.Func%602> を使用してデリゲートを呼び出し、デリゲートは値を返さないことに注意してください。  
  
 また、<xref:System.Activities.AsyncCodeActivity> は <xref:System.Activities.AsyncCodeActivity.Cancel%2A> のオーバーライドも提供します。 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> と <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> は必須のオーバーライドですが、<xref:System.Activities.AsyncCodeActivity.Cancel%2A> はオプションで、アクティビティを取り消したり中止したりするときに未処理の非同期状態を消去できるようにオーバーライドすることが可能です。 消去が可能で `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` が `true` の場合、アクティビティでは <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> を呼び出します。 このメソッドからスローされるすべての例外は、ワークフロー インスタンスにとって致命的なものです。  
  
 [!code-csharp[CFX_ActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>クラスでの非同期メソッドの呼び出し  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の多くのクラスには、非同期機能が用意されています。この非同期機能は、<xref:System.Activities.AsyncCodeActivity> ベースのアクティビティを使用して非同期に呼び出すことができます。 次の例では、アクティビティが作成を使用して非同期的にファイルを作成する、<xref:System.IO.FileStream>クラス。  
  
 [!code-csharp[CFX_ActivityExample#12](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>BeginExecute メソッドと EndExecute メソッドの間での状態の共有  
 前の例では、<xref:System.IO.FileStream> 内で作成した <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> オブジェクトに <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 内でアクセスしています。 このことは、`file` 変数を <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> 内で <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> のプロパティに渡すことで可能になっています。 これは <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> および <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> の間で状態を共有するための正しい方法です。 派生クラス内 (この場合は `FileWriter`) のメンバー変数を使用して <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> と <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> の間で状態を共有するのは正しい方法ではありません。そのようにすると、アクティビティのオブジェクトが複数のアクティビティ インスタンスから参照される可能性があります。 メンバー変数を使用して状態を共有すると、いずれかの <xref:System.Activities.ActivityInstance> の値が上書きされたり、別の <xref:System.Activities.ActivityInstance> の値が使用されたりする場合があります。  
  
### <a name="accessing-argument-values"></a>引数値へのアクセス  
 <xref:System.Activities.AsyncCodeActivity> の環境は、アクティビティに定義されている引数から構成されます。 これらの引数からアクセスできる、 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>上書きを使用して、<xref:System.Activities.AsyncCodeActivityContext>パラメーター。 デリゲート内で引数にアクセスすることはできませんが、デリゲートのパラメーターを使用すると、引数値や任意の他の必要なデータをデリゲートに渡すことができます。 次の例では、`Max` 引数から包含的上限を取得する乱数生成アクティビティを定義します。 デリゲートを呼び出すと、引数の値は非同期コードに渡されます。  
  
 [!code-csharp[CFX_ActivityExample#9](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>AsyncCodeActivity を使用した、アクションまたは子アクティビティのスケジュール設定  
 <xref:System.Activities.AsyncCodeActivity> 派生カスタム アクティビティはワークフローのスレッドに関する作業を非同期に実行するメソッドを提供しますが、子アクティビティやアクションをスケジュールする機能はありません。 ただし、非同期動作は、コンポジションを介して子アクティビティのスケジュール設定と組み合わせることができます。 非同期アクティビティを作成してから、<xref:System.Activities.Activity> または <xref:System.Activities.NativeActivity> の派生アクティビティと共に構成すると、子アクティビティまたはアクションの非同期動作とスケジュール機能を提供できます。 たとえば、アクティビティを <xref:System.Activities.Activity> から派生するように作成し、その実装時に <xref:System.Activities.Statements.Sequence> に非同期アクティビティと共にアクティビティのロジックを実装する他のアクティビティを含めることができます。 使用してアクティビティの作成の例について<xref:System.Activities.Activity>と<xref:System.Activities.NativeActivity>を参照してください[方法。アクティビティ作成](how-to-create-an-activity.md)と[アクティビティ作成オプション](activity-authoring-options-in-wf.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Action>
- <xref:System.Func%602>

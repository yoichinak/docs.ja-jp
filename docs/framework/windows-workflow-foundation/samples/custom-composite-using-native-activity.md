---
title: ネイティブ アクティビティを使用したカスタム複合
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 41a823ab00a2be0772a07b15d1292dbb4e8d1a6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005201"
---
# <a name="custom-composite-using-native-activity"></a>ネイティブ アクティビティを使用したカスタム複合
このサンプルでは、他の <xref:System.Activities.NativeActivity> オブジェクトをスケジュールしてワークフローの実行のフローを制御する <xref:System.Activities.Activity> を作成する方法を示します。 この方法を示すために、このサンプルでは一般的な制御フローである Sequence と While の 2 つを使用します。

## <a name="sample-details"></a>サンプルの詳細
 `MySequence` から始めるとき、最初に気付くことは、それが <xref:System.Activities.NativeActivity> から派生しているということです。 <xref:System.Activities.NativeActivity> は、<xref:System.Activities.Activity> メソッドに渡される <xref:System.Activities.NativeActivityContext> を介して、ワークフロー ランタイム一式を公開する `Execute` オブジェクトです。

 `MySequence` は、ワークフローの作成者によって設定された <xref:System.Activities.Activity> オブジェクトのパブリック コレクションを公開します。 ワークフローの実行前に、ワークフロー ランタイムがワークフローの各アクティビティに対して <xref:System.Activities.Activity.CacheMetadata%2A> メソッドを呼び出します。 このプロセスの実行中に、ランタイムによって、データのスコープや有効期間を管理するための親子のリレーションシップが確立されます。 既定の実装、<xref:System.Activities.Activity.CacheMetadata%2A>メソッドは、<xref:System.ComponentModel.TypeDescriptor>インスタンス クラス、`MySequence`型のパブリック プロパティを追加するアクティビティ<xref:System.Activities.Activity>または<xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> の子として、`MySequence`アクティビティ。

 アクティビティで子アクティビティのパブリック コレクションを公開するときは、それらの子アクティビティ間で状態を共有すると考えられます。 そのため、親アクティビティ (この場合は `MySequence`) で、子アクティビティがそれを実現するための変数のコレクションも公開することをお勧めします。 などの子アクティビティ、<xref:System.Activities.Activity.CacheMetadata%2A>メソッドは、型のパブリック プロパティを追加します。<xref:System.Activities.Variable>または<xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> に関連付けられた変数として、`MySequence`アクティビティ。

 `MySequence` の子によって操作されるパブリック変数に加えて、`MySequence` では、子の実行の進行状況を追跡する必要もあります。 これを実現するために、プライベート変数 `currentIndex` を使用します。 この変数は、`MySequence` アクティビティの <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> メソッド内に `MySequence` メソッドの呼び出しを追加することで、<xref:System.Activities.Activity.CacheMetadata%2A> 環境の一部として登録されています。 <xref:System.Activities.Activity>`MySequence` コレクションに追加された `Activities` オブジェクトは、この方法で追加された変数にアクセスできません。

 `MySequence` をランタイムで実行すると、ランタイムがその <xref:System.Activities.NativeActivity.Execute%2A> メソッドを呼び出し、<xref:System.Activities.NativeActivityContext> を渡します。 <xref:System.Activities.NativeActivityContext> は、引数と変数の逆参照と、他の <xref:System.Activities.Activity> オブジェクトや `ActivityDelegates` のスケジュールを行うランタイムに返すアクティビティのプロキシです。 `MySequence` は、`InternalExecute` メソッドを使用して、最初の子と後続のすべての子を単一のメソッドでスケジュールするロジックをカプセル化します。 このメソッドは、まず `currentIndex` を逆参照します。 `Activities` コレクションに含まれる数と等しい場合、シーケンスは終了し、アクティビティが処理をスケジュールせずに戻り、ランタイムによって状態が <xref:System.Activities.ActivityInstanceState.Closed> に変更されます。 場合、`currentIndex`が小さいから取得したは、次の子アクティビティの数よりも、`Activities`コレクションと`MySequence`呼び出し<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>、スケジュールする子を渡して、<xref:System.Activities.CompletionCallback>を指す、 `InternalExecute`メソッド。 最後に、`currentIndex` がインクリメントされ、制御がランタイムに戻されます。 `MySequence` のインスタンスで子 <xref:System.Activities.Activity> オブジェクトがスケジュールされていれば、ランタイムはそのインスタンスの状態が Executing であると見なします。

 子アクティビティが完了すると、<xref:System.Activities.CompletionCallback> が実行され、 ループが先頭から継続されます。 `Execute` と同様、<xref:System.Activities.CompletionCallback> は <xref:System.Activities.NativeActivityContext> を受け取り、実装側へのアクセスをランタイムに提供します。

 `MyWhile` 異なります`MySequence`単一のスケジュール<xref:System.Activities.Activity>オブジェクトを繰り返し、およびそれを使用して、 <xref:System.Activities.Activity%601>< bool\>という`Condition`このスケジュールを実行するかどうかを判断します。 `MySequence` と同様に、`MyWhile` でも、`InternalExecute` メソッドを使用してスケジュール ロジックを集中化しています。 スケジュール、 `Condition` <xref:System.Activities.Activity>< bool\>で、 <xref:System.Activities.CompletionCallback%601> \<bool > という名前の`OnEvaluationCompleted`します。 `Condition` の実行が完了すると、その結果を、この <xref:System.Activities.CompletionCallback> を通じて、`result` という名前の厳密に型指定されたパラメーターで使用できるようになります。 `true` の場合、`MyWhile` は <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> を呼び出し、`Body` として <xref:System.Activities.Activity>`InternalExecute` オブジェクトと <xref:System.Activities.CompletionCallback> を渡します。 `Body` の実行が完了すると、`Condition` でもう一度 `InternalExecute` がスケジュールされ、再度ループが開始されます。 `Condition` が `false` を返すと、`MyWhile` のインスタンスが `Body` をスケジュールせずに制御をランタイムに戻し、ランタイムによって状態が <xref:System.Activities.ActivityInstanceState.Closed> に変更されます。

#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. Visual Studio 2010 で Composite.sln サンプル ソリューションを開きます。

2. ソリューションをビルドして実行します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
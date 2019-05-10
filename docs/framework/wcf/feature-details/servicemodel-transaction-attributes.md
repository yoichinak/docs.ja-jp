---
title: ServiceModel トランザクションの属性
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
ms.openlocfilehash: 8f8a50dc82c073c9357209a4dbeeed6c8b075695
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586149"
---
# <a name="servicemodel-transaction-attributes"></a>ServiceModel トランザクションの属性
Windows Communication Foundation (WCF) の 3 つの標準のプロパティを提供<xref:System.ServiceModel>WCF サービスのトランザクションの動作を構成するための属性。  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## <a name="transactionflowattribute"></a>TransactionFlowAttribute  
 <xref:System.ServiceModel.TransactionFlowAttribute> 属性は、クライアントから受信トランザクションを受け入れるときのサービス コントラクトにおける操作の受け入れやすさを指定します。 属性は、次のプロパティを使用してこのコントロールを提供します。トランザクションを使用して、<xref:System.ServiceModel.TransactionFlowOption>受信トランザクションかどうかを指定する列挙体<xref:System.ServiceModel.TransactionFlowOption.Mandatory>、 <xref:System.ServiceModel.TransactionFlowOption.Allowed>、または<xref:System.ServiceModel.TransactionFlowOption.NotAllowed>します。  
  
 これは、サービス操作をクライアントの外部とのやり取りに関連付ける唯一の属性です。 次のセクションで説明する属性は、操作の実行内部におけるトランザクションの使用と関連しています。  
  
## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性は、サービス コントラクト実装の内部実行動作を指定します。 この属性のトランザクション固有のプロパティは次のとおりです。  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> は、セッションの終了時に、未完了のトランザクションを完了させるかどうかを指定します。 このプロパティの既定値は `false` です。 このプロパティが `true` で、ネットワークまたはクライアントの障害が原因で、入力セッションが終了せずにシャットダウンした場合は、すべての未完了のトランザクションが正常に完了します。 このプロパティが `false` の場合、またはセッションが正常に終了しなかった場合は、セッションの終了時にすべての未完了のトランザクションがロールバックされます。 このプロパティを `true` に設定する場合、受信チャネルはセッション ベースである必要があります。  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> は、トランザクションが完了したときに基になるサービス インスタンスを解放するかどうかを指定します。 このプロパティの既定値は `true` です。 次の受信メッセージによって、基になる新しいインスタンスが作成されると、以前のインスタンスが保持していたトランザクションごとの状態は破棄されます。 サービス インスタンスの解放はサービスが実行する内部動作であるため、クライアントが確立した既存の接続またはセッションに影響を及ぼすことはありません。 この機能は、COM+ に用意された Just-In-Time アクティベーション機能に相当します。 このプロパティが `true` の場合は、<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> と <xref:System.ServiceModel.ConcurrencyMode.Single> を一致させる必要があります。 そうでない場合、サービスの起動中に無効な構成の検証例外がスローされます。  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> は、サービスのトランザクションで使用する分離レベルを指定します。このプロパティは、<xref:System.Transactions.IsolationLevel> の値のいずれかに設定されます。 ローカルの分離レベル プロパティが、<xref:System.Transactions.IsolationLevel.Unspecified> 以外に設定されている場合は、受信トランザクションの分離レベルをこのローカルのプロパティの設定に一致させる必要があります。 そうでない場合、受信トランザクションは拒否され、クライアントにエラーが返されます。 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> が `true` であり、トランザクションがフローしていない場合、このプロパティによって、ローカルで作成されるトランザクションに使用する <xref:System.Transactions.IsolationLevel> の値が決まります。 <xref:System.Transactions.IsolationLevel> が <xref:System.Transactions.IsolationLevel.Unspecified> に設定されている場合は、<xref:System.Transactions.IsolationLevel><xref:System.Transactions.IsolationLevel.Serializable> が使用されます。  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> は、サービスで作成された新しいトランザクションを完了させる期間を指定します。 この期間が過ぎてもトランザクションが完了しない場合は、トランザクションは中止されます。 <xref:System.TimeSpan> は、<xref:System.Transactions.TransactionScope> が <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> に設定された任意の操作、および新しいトランザクションが作成された任意の操作の `true` タイムアウトとして使用されます。 このタイムアウトは、2 フェーズ コミット プロトコルにおいて、トランザクションが作成されてからフェーズ 1 が完了するまでの最大許容時間です。 使用されるタイムアウト値は、<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> プロパティと `transactionTimeout` 構成設定のうち、常に小さい方の値になります。  
  
## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute  
 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性は、サービス実装におけるメソッドの動作を指定します。 この属性を使用して、操作の特定の実行動作を示すことができます。 この属性のプロパティは、サービス コントラクトの Web サービス記述言語 (WSDL) の説明には影響しません、自体を実装するために開発者がそれ以外の場合がある一般的な機能を有効に、WCF プログラミング モデルの要素だけです。  
  
 この属性には、次のようなトランザクション固有のプロパティがあります。  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は、メソッドをアクティブなトランザクション スコープ内で実行する必要があるかどうかを指定します。 既定値は `false` です。 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性がメソッドに対して設定されていない場合は、そのメソッドがトランザクション内で実行されないことを意味します。 操作のトランザクション スコープが要求されない場合、メッセージ ヘッダーにあるトランザクションはアクティブ化されず、<xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> の <xref:System.ServiceModel.OperationContext> の要素として残ります。 操作のトランザクション スコープが必要な場合は、トランザクションのソースは次のいずれかから派生します。  
  
    - トランザクションがクライアントからフローされた場合、その分散トランザクションを使用して作成されたトランザクション スコープの下でメソッドが実行されます。  
  
    - キューに置かれたトランスポートでは、メッセージをキューから削除するトランザクションが使用されます。 使用されるトランザクションはフローされたトランザクションではなく、したがってメッセージの送信元によって提供されたものではないことに注意してください。  
  
    - カスタム トランスポートは、`TransportTransactionProperty` を使用することによってトランザクションを提供できます。  
  
    - 上記のいずれもがトランザクションの外部ソースを提供しない場合は、メソッドの呼び出しの直前に新規の <xref:System.Transactions.Transaction> インスタンスが作成されます。  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> は、未処理の例外がスローされなかった場合に、メソッドが実行されているトランザクションが自動的に完了されるかどうかを指定します。 このプロパティが `true` の場合は、ユーザー メソッドが例外をスローせずに復帰したときに、呼び出し側のインフラストラクチャが自動的にそのトランザクションを "完了" としてマークします。 このプロパティが `false` の場合、トランザクションはインスタンスにアタッチされ、このプロパティが `true` とマークされた後続のメソッドがクライアントによって呼び出されるか、または後続のメソッドから <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> が明示的に呼び出された場合にのみ、"完了" とマークされます。 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> プロパティを `true` に設定しない限り、これらのどちらの実行に失敗しても、トランザクションは "完了" にならなくなり、格納されている作業はコミットされません。 このプロパティが `true` に設定されている場合、セッションのあるチャネルを使用し、<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> を <xref:System.ServiceModel.InstanceContextMode.PerSession> に設定する必要があります。

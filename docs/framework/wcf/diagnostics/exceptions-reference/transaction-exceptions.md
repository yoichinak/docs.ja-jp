---
title: トランザクションの例外
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936981"
---
# <a name="transaction-exceptions"></a>トランザクションの例外
このトピックでは、Windows Communication Foundation (WCF) のトランザクションによって生成されたすべての例外を使用します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|メタデータからインポートされたポリシー情報により、TransactionProtocol に操作間で異なる値が指定されました。 各エンドポイントでサポートされる TransactionProtocol は 1 つに限られます。|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete は、サービスの InstanceContextMode が PerSession にならない限り、false にはなりません。 指定したコントラクトと操作の実装でエラーが発生しました。|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete は、TransactionAutoComplete が false に設定され、TransactionScopeRequired が true に設定されている場合にのみ、操作から呼び出すことができます。 これは無効なシナリオであり、現在のトランザクションは終了しました。|  
|TransactionFlowRequiredIssuedTokens|トランザクションをフローさせるには、発行済みトークンのフローもサポートされる必要があります。|  
|TrustDriverVersionDoesNotSupportIssuedTokens|構成されたバージョンの Trust では、発行済みトークンがサポートされません。 WSTrustFeb2005 またはそれ以降を使用してください。|

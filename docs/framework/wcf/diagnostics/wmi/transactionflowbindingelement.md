---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150086"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>メソッド  
 TransactionFlowBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 TransactionFlowBindingElement クラスには、次のプロパティがあります。  
  
### <a name="issuedtokens"></a>IssuedTokens  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 発行されるセキュリティ トークン ヘッダー (WS-Trust からの IssuedTokens) の要件を指定します。  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 トランザクションをフローさせるためにサービスによって使用されるトランザクション プロトコルです。  
  
### <a name="transactions"></a>トランザクション  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 受信トランザクションをサポートするかどうかを示します。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

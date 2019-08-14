---
title: '方法: サービス コントラクトでのエラーを宣言する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971967"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>方法: サービス コントラクトでのエラーを宣言する

マネージド コードでは、エラー条件が発生すると例外がスローされます。 ただし Windows Communication Foundation (WCF) アプリケーションでは、サービスコントラクトは、サービスコントラクトで SOAP エラーを宣言することで、クライアントに返されるエラー情報を指定します。 例外とエラーの関係の概要については、「[コントラクトとサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>SOAP エラーを指定するサービス コントラクトを作成する

1. サービス コントラクトを作成し、操作をいくつか定義します。 例については、「[方法: サービスコントラクト](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)を定義します。

2. 操作を選択します。これに対して指定したエラー条件が発生したとき、クライアント側に通知することになります。 SOAP エラーをクライアントに返す原因となるエラー条件を判断するには、「[コントラクトとサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。

3. 選択した操作に対して <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> 属性を適用し、シリアル化可能なエラー型をコンストラクターに渡します。 シリアル化可能な型の作成と使用の詳細については、「[サービスコントラクトでのデータ転送の指定](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)」を参照してください。 `SampleMethod` 操作で `GreetingFault` を返せるように指定する例を次に示します。

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. コントラクト内でクライアントへの通知が必要な操作すべてについて、手順 2. および 3. を繰り返します。

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>指定した SOAP エラーを返す操作の実装
 エラー状態を呼び出し元アプリケーションに通知するために、前の手順で指定したような特定の SOAP エラーを操作中に返せるように指定したので、次に実際に通知処理を実装します。

### <a name="throw-the-specified-soap-fault-in-the-operation"></a>指定した SOAP エラーを操作中に例外としてスローする

1. 操作中に <xref:System.ServiceModel.FaultContractAttribute> で指定したエラー条件が発生したとき、<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> 例外を生成してスローする、というコードを記述します。SOAP エラーは型パラメーターとして、生成する例外に渡します。 前の手順で示した `GreetingFault` 内で `SampleMethod` 例外をスローするコード例を次に示します。

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a>例

`GreetingFault` 操作内で `SampleMethod` エラーが発生した場合の処理を実装したコード例を次に示します。

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>

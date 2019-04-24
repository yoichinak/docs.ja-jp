---
title: サービス コントラクトの実装
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196321"
---
# <a name="implementing-service-contracts"></a>サービス コントラクトの実装
サービスは、1 つ以上のエンドポイントでクライアントが使用できる機能を公開するクラスです。 サービスを作成するには、Windows Communication Foundation (WCF) コントラクトを実装するクラスを記述します。 2 つの方法のいずれかでこれを行うことができます。 コントラクトを個別にインターフェイスとして定義し、そのインターフェイスを実装するクラスを作成できます。 または、クラスに <xref:System.ServiceModel.ServiceContractAttribute> 属性を配置し、サービスのクライアントが使用できるメソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性を配置することによって、クラスとコントラクトを直接作成することもできます。  
  
## <a name="creating-a-service-class"></a>サービス クラスの作成  
 個別に定義された `IMath` コントラクトを実装するサービスの例を次に示します。  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 また、サービスは直接コントラクトを公開できます。 `MathService` コントラクトを定義し、実装するサービス クラスの例を次に示します。  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 コントラクト名が異なるので、上記の 2 つのサービスが公開するコントラクトはそれぞれ異なります。 最初の例では、公開されるコントラクトの名前が "`IMath`" であるのに対し、2 番目の例では、コントラクトの名前は "`MathService`" です。  
  
 コンカレンシーやインスタンス化など、いくつかの項目は、サービス実装レベルと操作実装レベルで設定できます。 詳細については、次を参照してください。[のデザインと実装サービス](../../../docs/framework/wcf/designing-and-implementing-services.md)します。  
  
 サービス コントラクトを実装したら、そのサービスに 1 つ以上のエンドポイントを作成する必要があります。 詳細については、次を参照してください。[エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)します。 サービスを実行する方法の詳細については、次を参照してください。[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)します。  
  
## <a name="see-also"></a>関連項目

- [サービスの設計と実装](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [方法: コントラクト クラスを使用して、サービスを作成します。](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [方法: サービス コントラクト インターフェイスを作成します。](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [サービスのランタイム動作の指定](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)

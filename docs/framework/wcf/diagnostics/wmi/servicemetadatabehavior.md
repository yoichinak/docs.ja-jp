---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976138"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceMetadataBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceMetadataBehavior クラスには、次のプロパティがあります。  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 サービスがメタデータ要求をリダイレクトする場所を設定します。  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 `HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 `HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

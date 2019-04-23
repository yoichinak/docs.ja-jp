---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 2e38eb2c2d42ffc5436562b254a42215ccabbab2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768658"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceDebugBehavior クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 ServiceDebugBehavior クラスには、次のプロパティがあります。  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 `HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 `HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージド例外情報を含めるかどうかを指定します。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>

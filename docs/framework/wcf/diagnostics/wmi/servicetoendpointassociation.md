---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048232"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
エンドポイントにサービスを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceToEndpointAssociation クラスには、次のプロパティがあります。  
  
### <a name="ref"></a>ref  
 データの種類:サービス  
  
 アクセスの種類:読み取り専用です。  
修飾子:キー  
  
 エンドポイントに関連付けられるサービス。  
  
### <a name="ref"></a>ref  
 データの種類:エンドポイント  
  
 アクセスの種類:読み取り専用です。  
修飾子:キー  
  
 サービスに関連付けられるエンドポイント。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|

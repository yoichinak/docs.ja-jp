---
title: AspNetCompatibilityRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 00908a39-a21b-4029-bbb9-33e5a6ed25a7
ms.openlocfilehash: 8e4b2e0e32ccd3b671e81531833ccb3aa3788389
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199987"
---
# <a name="aspnetcompatibilityrequirementsattribute"></a>AspNetCompatibilityRequirementsAttribute
AspNetCompatibilityRequirementsAttribute  
  
## <a name="syntax"></a>構文  
  
```csharp
class AspNetCompatibilityRequirementsAttribute : Behavior  
{  
  string RequirementsMode;  
};  
```  
  
## <a name="methods"></a>メソッド  
 AspNetCompatibilityRequirementsAttribute クラスは、メソッドをすべて定義しません。  
  
## <a name="properties"></a>プロパティ  
 AspNetCompatibilityRequirementsAttribute クラスには、次のプロパティがあります。  
  
### <a name="requirementsmode"></a>RequirementsMode  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 Asp.Net 互換モードがアクティブであるかどうかを示します。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceHostingEnvironment.AspNetCompatibilityEnabled%2A>

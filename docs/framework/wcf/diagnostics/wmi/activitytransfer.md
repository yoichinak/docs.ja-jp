---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662823"
---
# <a name="activitytransfer"></a>ActivityTransfer
アクティビティ転送イベント  
  
## <a name="syntax"></a>構文  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ActivityTransfer クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ActivityTransfer クラスには次のプロパティがあります。  
  
### <a name="activityid"></a>ActivityID  
  
- データ型: object  
    アクセスの種類:読み取り専用  
  
- アクティビティ ID  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- データ型: object  
    アクセスの種類:読み取り専用  
  
- 関連アクティビティ ID  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|

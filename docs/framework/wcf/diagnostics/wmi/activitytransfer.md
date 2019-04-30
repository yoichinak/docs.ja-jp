---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964296"
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

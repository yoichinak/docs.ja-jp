---
title: COR_GC_REFERENCE 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1e31e95473136bf7e7c196eacc278fa8a1caab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093658"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE 構造体
ガベージ コレクトされるオブジェクトに関する情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`domain`|ハンドルまたはオブジェクトが所属するアプリケーション ドメインへのポインター。 その値があります`null`します。|  
|`location`|ICorDebugValue またはガベージ コレクトされるオブジェクトに対応する ICorDebugReferenceValue インターフェイスのいずれか。|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)ルートの出所を示す列挙値。 詳細については、「解説」を参照してください。|  
|`extraData`|ガベージ コレクトされるオブジェクトに関する追加データ。 この情報は、によって示される、オブジェクトのソースとは異なります。、`type`フィールド。 詳細については、「解説」を参照してください。|  
  
## <a name="remarks"></a>Remarks  
 `type`フィールドは、 [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)参照の出所を示す列挙値。 特定の`COR_GC_REFERENCE`値は次のようなマネージ オブジェクトのいずれかを反映できます。  
  
-   すべてのマネージ スタックからオブジェクト (`CorGCReferenceType.CorReferenceStack`)。 これには、共通言語ランタイムによって作成されたオブジェクトと同様に、マネージ コードでのライブ参照が含まれます。  
  
-   オブジェクト ハンドル テーブルから (`CorGCReferenceType.CorHandle*`)。 強い参照が含まれます (`HNDTYPE_STRONG`と`HNDTYPE_REFCOUNT`) とモジュールの静的変数。  
  
-   ファイナライザー キューからオブジェクト (`CorGCReferenceType.CorReferenceFinalizer`)。 ファイナライザー キューでは、ファイナライザーが実行されるまでオブジェクトがルートします。  
  
 `extraData`フィールドには参照のソース (または型) によって追加のデータが含まれています。 指定できる値は次のとおりです。  
  
-   `DependentSource`. 場合、`type`は`CorGCREferenceType.CorHandleStrongDependent`、このフィールドはオブジェクトでガベージ コレクトされるオブジェクトの場合は、ルートを`COR_GC_REFERENCE.Location`します。  
  
-   `RefCount`. 場合、`type`は`CorGCREferenceType.CorHandleStrongRefCount`、このフィールドは、ハンドルの参照カウントします。  
  
-   `Size`. 場合、`type`は`CorGCREferenceType.CorHandleStrongSizedByref`、このフィールドは、ガベージ コレクターがオブジェクトのルートを計算するオブジェクト ツリーの最後のサイズ。 この計算は必ずしも最新ではないことに注意してください。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

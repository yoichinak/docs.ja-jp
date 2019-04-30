---
title: CLR_DEBUGGING_VERSION 構造体
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87f938a7119abe4a88da65bd779a5f4a02499516
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996347"
---
# <a name="clrdebuggingversion-structure"></a>CLR_DEBUGGING_VERSION 構造体
デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`wStructVersion`|構造のバージョン番号|  
|`wMajor`|メジャー バージョン番号。|  
|`wMinor`|マイナー バージョン番号。|  
|`wBuild`|ビルド番号。|  
|`wRevision`|リビジョン番号。|  
  
## <a name="remarks"></a>Remarks  
 `CLR_DEBUGGING_VERSION`構造がただし COR_VERSION 構造体と同じでは、`CLR_DEBUGGING_VERSION`構造は追加の構造のバージョン フィールドを提供します (`wStructVersion`)。 現時点では、このフィールドは 0 に設定する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

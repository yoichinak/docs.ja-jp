---
title: ICorDebugEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e2d7a344cabb1ab816e4fe696ebb47276397ec3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774557"
---
# <a name="icordebugenumskip-method"></a>ICorDebugEnum::Skip メソッド
指定数の項目では、列挙体にカーソルを移動します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `celt`  
 [in]カーソルを前方に移動する項目の数。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)

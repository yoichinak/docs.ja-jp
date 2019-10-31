---
title: ICorDebugModule::IsDynamic メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 5774b40178ce0d7c2ef5d063a37b9011fc2630df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127943"
---
# <a name="icordebugmoduleisdynamic-method"></a>ICorDebugModule::IsDynamic メソッド
このモジュールが動的かどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pDynamic`  
 [out] このモジュールが動的である場合は `true`。それ以外の場合は、`false`ます。  
  
## <a name="remarks"></a>Remarks  
 動的モジュールは、モジュールが読み込まれた後でも、新しいクラスを追加したり、既存のクラスを削除したりできます。 は、クラスが追加または削除されたときに、 [UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) [Callback:: loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)コールバックとによって、デバッガーに通知します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

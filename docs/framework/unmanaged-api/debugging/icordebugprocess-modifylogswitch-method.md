---
title: ICorDebugProcess::ModifyLogSwitch メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 86b8737577bdb5f61f1061cb217620fae03ebd0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139376"
---
# <a name="icordebugprocessmodifylogswitch-method"></a>ICorDebugProcess::ModifyLogSwitch メソッド
指定されたログスイッチの重大度レベルを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pLogSwitchName`  
 からログスイッチの名前を指定する文字列へのポインター。  
  
 `lLevel`  
 から指定されたログスイッチに設定される重大度レベル。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、によって実行される場合にのみ有効です: [: CreateProcess managedcallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバックが発生しました。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

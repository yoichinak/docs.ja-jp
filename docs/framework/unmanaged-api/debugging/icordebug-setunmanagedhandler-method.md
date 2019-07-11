---
title: ICorDebug::SetUnmanagedHandler メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50a4bedfee0c402bb76265371d3b9809263ef97
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738140"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler メソッド
非管理対象のイベントのイベント ハンドラー オブジェクトを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pCallback`  
 [in]ポインター、 [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)非管理対象のイベントのイベント ハンドラーを表すオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 イベント ハンドラー オブジェクトのアンマネージ呼び出しの後にイベントを設定する必要があります[icordebug::initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)と呼び出しの前に[icordebug::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)または[icordebug::debugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). ただし、レガシー目的のための必要はありません、最初のネイティブ デバッグ イベントが発生するまでの非管理対象のイベントのイベントのハンドラー オブジェクトを設定します。 具体的には場合、`ICorDebug::CreateProcess`ネイティブ デバッグのメイン スレッドが再開されるまで、イベントをディスパッチすることはできません、CREATE_SUSPENDED フラグが設定されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

---
title: ICorDebug::DebugActiveProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 5b988b110100cd159b8e262573df409847d635c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134122"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess メソッド
デバッガーを既存のプロセスにアタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `id`  
 からデバッガーがアタッチされるプロセスの ID。  
  
 `win32Attach`  
 からデバッガーがプロセスの Win32 デバッガーとして動作し、アンマネージコールバックをディスパッチする必要がある場合に `true` に設定されるブール値。それ以外の場合は、`false`ます。  
  
 `ppProcess`  
 入出力デバッガーがアタッチされているプロセスを表す "いいプロセス" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 相互運用デバッグは、IA-64 ベースおよび AMD64 ベースのプラットフォームなど、Win9x および x86 以外のプラットフォームではサポートされていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

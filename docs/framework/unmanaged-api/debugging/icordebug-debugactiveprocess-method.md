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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b3869c9f96eee6f0e3066a99a58a154a2f5f2ee
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480092"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess メソッド
既存のプロセスにデバッガーをアタッチします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `id`  
 [in]デバッガーのアタッチ先のプロセスの ID。  
  
 `win32Attach`  
 [in]ブール値に設定されている`true`デバッガーで、Win32 のデバッガー プロセスとして動作する必要があります、アンマネージのコールバックのディスパッチ場合それ以外の場合、`false`します。  
  
 `ppProcess`  
 [out]デバッガーのアタッチするプロセスを表す"ICorDebugProcess"オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 IA 64 ベースおよび AMD64 ベースのプラットフォームなど、Win9x と x86 以外のプラットフォームでは、相互運用機能デバッグはサポートされていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

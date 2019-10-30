---
title: ICorDebugMDA::GetXML メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: f80bdffbf5c0ba39980bd27c6e89a368547340c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129809"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML メソッド
[によって](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)表されるマネージデバッグアシスタント (MDA) に関連付けられた完全な XML ストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cchName`  
 [in] `szName` 配列のサイズ。  
  
 `pcchName`  
 入出力XML ストリームの長さへのポインター。  
  
 `szName`  
 入出力XML ストリームを格納する配列。 配列が空である可能性があります。  
  
## <a name="remarks"></a>Remarks  
 `GetXML` メソッドは、関連付けられている XML ストリームのサイズによっては、パフォーマンスに影響する可能性があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMDA インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [マネージド デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

---
title: ICorDebugProcess::EnumerateAppDomains メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: e09e25503ad00ab3542f0c4f50221b6014b25561
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128879"
---
# <a name="icordebugprocessenumerateappdomains-method"></a>ICorDebugProcess::EnumerateAppDomains メソッド
このプロセス内のすべてのアプリケーションドメインを列挙します。  
  
## <a name="syntax"></a>構文  
  
``` cpp 
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppAppDomains`  
 入出力このプロセス内のアプリケーションドメインの列挙子である[ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)のアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 このメソッド[は、によって](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)使用できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

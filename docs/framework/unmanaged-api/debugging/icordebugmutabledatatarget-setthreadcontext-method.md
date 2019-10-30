---
title: 'ICorDebugMutableDataTarget:: SetThreadContext メソッド'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 2c9e508c7a4059fee4e1cce6eb28e6de7b2fff6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132704"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget:: SetThreadContext メソッド
スレッドのコンテキスト (レジスタの値) を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwThreadID`  
 [in] オペレーティング システム定義のスレッド識別子。  
  
 `contextSize`  
 [in]書き込まれる `pContext` バッファーのサイズ。  
  
 `pContext`  
 [in]書き込まれるバイト数へのポインター。  
  
## <a name="remarks"></a>Remarks  
 `SetThreadContext` メソッドは、オペレーティング システム定義の `dwThreadID` 引数で指定されるスレッドの現在のコンテキストを更新します。 コンテキストレコードの形式は、のプラットフォームによって決定されます。このプラットフォームでは、次[のように](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)指定します。 Windows では、これは[コンテキスト](/windows/win32/api/winnt/ns-winnt-arm64_nt_context)構造です。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMutableDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

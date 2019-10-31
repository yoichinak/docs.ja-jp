---
title: ICorDebugExceptionObjectCallStackEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: 99a700270794ca92356cb9d134cb869d456199f9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084428"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum インターフェイス
例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。 このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[いい Exceptionobjectcallstackenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|例外オブジェクトの呼び出し履歴に関する情報を格納している、指定した数の[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)オブジェクトを取得します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugExceptionObjectCallStackEnum` インターフェイスは、ICorDebugEnum インターフェイスを実装します。  
  
 [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)オブジェクトには、EnumerateExceptionCallStack メソッドを呼び出すことによって[値](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)が設定されます。 `ICorDebugExceptionObjectCallStackEnum` コレクション内のコールスタック項目を列挙するには、[次](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)のように指定します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

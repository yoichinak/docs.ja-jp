---
title: ICorDebugFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124073"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame インターフェイス

現在のスタックのフレームを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateStepper メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|この `ICorDebugFrame`に対して、ステップ実行操作を実行する ICorDebugStepper を取得します。|  
|[GetCallee メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|このフレームが呼び出された現在のチェーン内の `ICorDebugFrame` へのポインターを取得します。または、このがチェーン内の最も内側のフレームである場合は null を返します。|  
|[GetCaller メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|このフレームを呼び出した現在のチェーン内の `ICorDebugFrame` へのポインターを取得します。これがチェーンの最も外側のフレームである場合は null を返します。|  
|[GetChain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|この `ICorDebugFrame` が含まれている、このチェーンへのポインターを取得します。|  
|[GetCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|このスタックフレームに関連付けられているテキストコードへのポインターを取得します。|  
|[GetFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|このスタックフレームに関連付けられているコードを格納しているコードを指すポインターを取得します。|  
|[GetFunctionToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|このスタックフレームに関連付けられているコードを含む関数のメタデータトークンを取得します。|  
|[GetStackRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|この `ICorDebugFrame`によって表されるスタックフレームの絶対アドレス範囲を取得します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

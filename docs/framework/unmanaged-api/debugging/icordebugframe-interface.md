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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a15d7f16676b8b9d66f8d1ba7484f3fec5735a44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988755"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame インターフェイス

現在のスタックのフレームを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateStepper メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|この基準としたステップ実行操作を実行する、ICorDebugStepper を取得します。`ICorDebugFrame`します。|  
|[GetCallee メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|ポインターを取得、`ICorDebugFrame`このフレームで呼び出されると、この場合は null を返しますが、チェーン内の最も内側のフレームには、現在のチェーンでします。|  
|[GetCaller メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|ポインターを取得、`ICorDebugFrame`というがこのフレームでは、現在のチェーン内か、この場合は null を返しますが、チェーン内の最も外側のフレーム。|  
|[GetChain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|この、ICorDebugChain へのポインターを取得します。`ICorDebugFrame`の一部です。|  
|[GetCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|このスタック フレームに関連付けられている ICorDebugCode にポインターを取得します。|  
|[GetFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|このスタック フレームに関連付けられているコードを含む ICorDebugFunction にポインターを取得します。|  
|[GetFunctionToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|このスタック フレームに関連付けられているコードを含む関数のメタデータ トークンを取得します。|  
|[GetStackRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|これによって表されるスタック フレームの絶対アドレス範囲を取得`ICorDebugFrame`します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

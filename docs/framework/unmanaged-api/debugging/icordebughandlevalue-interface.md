---
title: ICorDebugHandleValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915004"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue インターフェイス

デバッガーがガベージコレクションのハンドルを作成した参照値を表す、値のサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dispose メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|インターフェイスポインターを明示的に`ICorDebugHandleValue`解放せずに、このオブジェクトによって参照されるハンドルを解放します。|  
|[GetHandleType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|この`ICorDebugHandleValue`によって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得します。|  
  
## <a name="remarks"></a>Remarks  
 デバッグ`ICorDebugReferenceValue`対象のコードの実行が中断された場合、オブジェクトは無効になります。 は`ICorDebugHandleValue` 、明示的に解放されるまで、中断および継続による参照を保持します。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

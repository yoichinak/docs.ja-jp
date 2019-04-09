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
ms.openlocfilehash: 9a9eb63e681b47f058901b0ff002015baffe6048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117444"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue インターフェイス

参照値が、デバッガーにガベージ コレクションのハンドルが作成を表すサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dispose メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|これによって参照されるハンドルを解放`ICorDebugHandleValue`インターフェイス ポインターを明示的に解放しないままオブジェクト。|  
|[GetHandleType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|これによって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得します`ICorDebugHandleValue`します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugReferenceValue`オブジェクトがデバッグ対象のコードの実行の中断によって無効にします。 `ICorDebugHandleValue`明示的に解放されるまでの区切りと継続のうち、その参照を保持します。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

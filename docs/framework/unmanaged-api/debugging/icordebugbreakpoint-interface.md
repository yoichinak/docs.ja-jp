---
title: ICorDebugBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a68e061c6def61746ee65f8a25818f8dbcd785b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159732"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint インターフェイス

関数、または値のウォッチ ポイントでのブレークポイントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Activate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|このアクティブな状態を設定`ICorDebugBreakpoint`します。|  
|[IsActive メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|示す値を取得するかどうかこの`ICorDebugBreakpoint`がアクティブです。|  
  
## <a name="remarks"></a>Remarks  
 ブレークポイントは、条件式を直接はサポートしていません。 デバッガーがの上で実装する必要がありますこのような機能を使用する場合は、`ICorDebugBreakpoint`します。  
  
 ICorDebugFunctionBreakpoint インターフェイスは、拡張`ICorDebugBreakpoint`関数内のブレークポイントをサポートするためにします。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

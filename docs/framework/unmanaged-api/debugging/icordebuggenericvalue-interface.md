---
title: ICorDebugGenericValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 312b8b005998da44feb5ae24ab4a0a17bb948a3f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138569"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue インターフェイス

すべての値に適用される "ICorDebugValue" のサブクラス。 このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|指定したバッファーに値をコピーします。|  
|[SetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|指定したバッファーから新しい値をコピーします。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugGenericValue` は、リモート処理が不可能なため、サブインターフェイスです。  
  
 参照型の場合、値は参照の内容ではなく参照です。  
  
 このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

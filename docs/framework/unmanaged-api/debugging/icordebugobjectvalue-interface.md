---
title: ICorDebugObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0ac91681313b60ebfcaf725dcc2e0d6547e3c1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222615"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue インターフェイス

オブジェクトを含む値を表す"ICorDebugValue"のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|共通言語ランタイム (CLR) へのインターフェイス ポインターを取得<xref:System.Type>オブジェクトのこの`ICorDebugObjectValue`参照。|  
|[GetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|実装されていません。|  
|[GetFieldValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|インターフェイス ポインターを取得、 [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)指定したクラスの指定したフィールドの値を表します。|  
|[GetManagedCopy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|互換性のために残されています。 このメソッドを呼び出さないでください。|  
|[GetVirtualMethod メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|実装されていません。|  
|[IsValueClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|これによって、オブジェクトが参照されるかどうかを示す値を取得します`ICorDebugObjectValue`は値型です。|  
|[SetFromManagedCopy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|互換性のために残されています。 このメソッドを呼び出さないでください。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugObjectValue`デバッグ中の処理を続行するまで有効なままになります。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

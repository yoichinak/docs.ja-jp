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
ms.openlocfilehash: a4ca59aac075a42294026ad54c5d5dd4dbf7fda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943336"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue インターフェイス

オブジェクトを含む値を表す "ICorDebugValue" のサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<xref:System.Type> この`ICorDebugObjectValue`が参照するオブジェクトの共通言語ランタイム (CLR) へのインターフェイスポインターを取得します。|  
|[GetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|実装されていません。|  
|[GetFieldValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|指定したクラスの指定したフィールドの値を表す、 [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)へのインターフェイスポインターを取得します。|  
|[GetManagedCopy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|互換性のために残されています。 このメソッドを呼び出さないでください。|  
|[GetVirtualMethod メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|実装されていません。|  
|[IsValueClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|この`ICorDebugObjectValue`によって参照されるオブジェクトが値型かどうかを示す値を取得します。|  
|[SetFromManagedCopy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|互換性のために残されています。 このメソッドを呼び出さないでください。|  
  
## <a name="remarks"></a>Remarks  
 は、デバッグ中のプロセスが続行されるまで有効なままです。`ICorDebugObjectValue`  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

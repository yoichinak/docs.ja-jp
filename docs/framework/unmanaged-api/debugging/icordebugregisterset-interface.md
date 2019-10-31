---
title: ICorDebugRegisterSet インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 1ea0274adc12f3a99df0422bfc0b5180f0ef5596
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131379"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet インターフェイス
現在コードを実行しているコンピューターで使用できるレジスタのセットを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRegisters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。|  
|[GetRegistersAvailable メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|この `ICorDebugRegisterSet` 内のどのレジスタが現在使用可能であるかを示すビットマスクを取得します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|現在のスレッドのコンテキストを取得します。|  
|[SetRegisters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|.NET Framework バージョン2.0 には実装されていません。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2.0 には実装されていません。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugRegisterSet` インターフェイスでは、32ビットのレジスタのみがサポートされます。 追加のレジスタを必要とする IA-64 などのプラットフォームで[ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)インターフェイスを使用します。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

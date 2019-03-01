---
title: ICorDebugNativeFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbdb17bcd502b75da0a73d9a36cf36d6564320bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975486"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame インターフェイス

ネイティブ フレームで使用される ICorDebugFrame の特殊な実装です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|命令ポインターをネイティブ コードで指定されたオフセット位置に設定しても安全であるかどうかを示す値を取得します。|  
|[GetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|ネイティブ コードには、スタック フレームのオフセットを取得します。|  
|[GetLocalDoubleRegisterValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|引数またはネイティブ フレームの 2 つのメモリ レジスタに格納されているローカル変数の値を表す ICorDebugValue へのポインターを取得します。|  
|[GetLocalMemoryRegisterValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|ポインターを取得、`ICorDebugValue`うち下位ビットが指定されたレジスタに格納されている、上位ビットが指定されたメモリ アドレスに格納されている、ローカル変数の値を表します。|  
|[GetLocalMemoryValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|ポインターを取得、`ICorDebugValue`を表す、指定されたメモリ アドレスに格納されているローカル変数の値。|  
|[GetLocalRegisterMemoryValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|ポインターを取得、`ICorDebugValue`うち上位ビットが指定されたレジスタに格納されているし、指定されたメモリ アドレスの下位ビットが格納されている、ローカル変数の値を表す|  
|[GetLocalRegisterValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|ポインターを取得、`ICorDebugValue`引数または指定されたネイティブ レジスタに格納されているローカル変数の値を表します。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|ポインターを取得、 [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)これのレジスタ セットを表す`ICorDebugNativeFrame`します。|  
|[SetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|命令ポインターをネイティブ コードで指定されたオフセット位置に設定します。|  
  
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

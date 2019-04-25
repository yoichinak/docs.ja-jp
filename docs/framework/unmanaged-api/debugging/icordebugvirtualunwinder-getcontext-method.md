---
title: ICorDebugVirtualUnwinder::GetContext メソッド
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3125fd5081e68237714bcb10f760b73ce7509f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119227"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext メソッド
このアンワインダーの現在のコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `contextFlags`  
 [in] (WinNT.h で定義されている) コンテキストのどの部分を返すかを指定するフラグ。  
  
 `cbContextBuf`  
 [in] `contextBuf` のバイト数。  
  
 `contextSize`  
 [out] `contextBuf` に実際に書き込まれたバイト数へのポインター。  
  
 `contextBuf`  
 [out] このアンワインダーの現在のコンテキストが格納されているバイト配列。  
  
## <a name="return-value"></a>戻り値  
 mscordbi によって受信された失敗を示す HRESULT 値は致命的と見なされ、ICorDebug API によって `CORDBG_E_DATA_TARGET_ERROR` が返されます。  
  
## <a name="remarks"></a>Remarks  
 初期値を設定する、`contextBuf`呼び出すことによって返されるコンテキスト バッファーへの引数、 [icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)メソッド。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
 アンワインドではレジスタのサブセット (例: 不揮発性レジスタのみ) だけが復元されるため、コンテキストが、実際のメソッド呼び出し時点でのレジスタの状態と正確には一致しないことがあります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMemoryBuffer インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

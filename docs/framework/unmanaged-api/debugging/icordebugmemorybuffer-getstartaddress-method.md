---
title: 'GetStartAddress Memorybuffer:: メソッド'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1394624051baa9e7dd21e29788d5fab28332081b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987544"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a>GetStartAddress Memorybuffer:: メソッド
メモリ バッファーの開始アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [out] メモリ バッファーの開始アドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!WARNING]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMemoryBuffer インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

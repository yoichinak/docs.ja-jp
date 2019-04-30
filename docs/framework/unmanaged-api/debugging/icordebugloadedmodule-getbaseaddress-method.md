---
title: ICorDebugLoadedModule::GetBaseAddress メソッド
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e84d6deca0cd09cc547636007208c70ab91c1ab1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946287"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a>ICorDebugLoadedModule::GetBaseAddress メソッド
読み込まれたモジュールのベース アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAddress`  
 [out] 読み込まれたモジュールのベース アドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugLoadedModule インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

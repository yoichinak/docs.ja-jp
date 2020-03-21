---
title: ICorDebugDataTarget2::GetSymbolProviderForImage メソッド
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 500d36b414be686071990a6e1b40dd8759d02ae9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178929"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a>ICorDebugDataTarget2::GetSymbolProviderForImage メソッド
モジュールのベース アドレスからそのモジュールのシンボル プロバイダーを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `imageBaseAddress`  
 [in]モジュールのベース アドレスを表す[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)値。  
  
 `ppSymProvider`  
 [アウト][オブジェクトの](icordebugsymbolprovider-interface.md)アドレスへのポインター。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget2 インターフェイス](icordebugdatatarget2-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)

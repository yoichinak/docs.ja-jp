---
title: Icordebugsymbolprovider::gettypeprops メソッド
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 435a814d20e039c794f4f9eeb024d5afbfcd6dbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771188"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>Icordebugsymbolprovider::gettypeprops メソッド
Vtable の指定の相対仮想アドレス (RVA) における、ジェネリック パラメーターのシグネチャの数などの型のプロパティに関する情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tableRva`  
 [in] vtable の相対仮想アドレス (RVA)。  
  
 `cbSignature`  
 [in] `signature` 配列のサイズ。 「解説」を参照してください。  
  
 `pcbSignature`  
 [out] [out] 返される `signature` 配列のサイズへのポインター。  
  
 `signature`  
 [out] すべてのジェネリック パラメーターの typespec シグネチャを保持するバッファー。  
  
## <a name="remarks"></a>Remarks  
 必要な型のサイズを取得する`signature`配列は、設定、`cbSignature`引数を 0 にし、`signature`に**null**。 このメソッドから制御が戻ると、`pcbSignature` には `signature` 配列の必要なバイト数が格納されます。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetMethodProps メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

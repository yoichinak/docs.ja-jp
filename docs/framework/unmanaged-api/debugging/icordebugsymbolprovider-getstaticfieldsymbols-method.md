---
title: 'いいね Provider:: GetStaticFieldSymbols メソッド'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 8c4211a60786016e25cc3e3419804817b57ab64e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138806"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a>いいね Provider:: GetStaticFieldSymbols メソッド
typespec シグネチャに対応する静的フィールド シンボルを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cbSignature`  
 [in] `typeSig` 配列のバイト数。  
  
 `typeSig`  
 [in] `typespec` シグネチャを格納するバイト配列。  
  
 `cRequestedSymbols`  
 [in] 要求されるシンボルの数。  
  
 `pcFetchedSymbols`  
 [out] メソッドによって取得されたシンボル数へのポインター。  
  
 `pSymbols`  
 入出力要求された静的なフィールドシンボルが格納されている、表示名のある[シンボル](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)配列へのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetInstanceFieldSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [ICorDebugSymbolProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

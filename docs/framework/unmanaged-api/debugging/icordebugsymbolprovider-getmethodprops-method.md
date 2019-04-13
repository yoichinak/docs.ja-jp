---
title: ICorDebugSymbolProvider::GetMethodProps メソッド
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 784fcb10e9c0c3c6ff50c25d47bb4fb3fd5762ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161110"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps メソッド
メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのプロパティに関する情報 (メソッドのメタデータ トークンなど) と、そのジェネリック パラメーターに関する情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `codeRVA`  
 [in]情報を取得するメソッドでの相対仮想アドレス。  
  
 `pMethodToken`  
 [out] メソッドのメタデータ トークンへのポインター。  
  
 `pcGenericParams`  
 [out] このメソッドに関連付けられているジェネリック パラメーターの数へのポインター。  
  
 `cbSignature`  
 [in] `signature` 配列のサイズ。 「解説」を参照してください。  
  
 `pcbSignature`  
 [out] 返される `signature` 配列のサイズへのポインター。  
  
 `signature`  
 [out] すべてのジェネリック パラメーターの typespec シグネチャを保持するバッファー。  
  
## <a name="remarks"></a>Remarks  
 メソッドに必要なサイズを取得する`signature`配列は、設定、`cbSignature`引数を 0 にし、`signature`に**null**します。 このメソッドから制御が戻ると、`pcbSignature` には `signature` 配列の必要なバイト数が格納されます。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetTypeProps メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

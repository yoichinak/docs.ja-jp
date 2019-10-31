---
title: 'ICorDebugSymbolProvider2:: Getフレーム Props メソッド'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: 39bdb93fcb48da6667d982ca2d511ee5e499ae32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133642"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2:: Getフレーム Props メソッド
メソッドのメソッド開始位置を示す相対仮想アドレスと、指定されたコード相対仮想アドレスを持つ親フレームを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `codeRva`  
 [in] コード相対仮想アドレス。  
  
 `pCodeStartRva`  
 [out] メソッドの開始相対仮想アドレスへのポインター。  
  
 `pParentFrameStartRva`  
 [out] フレームの開始相対仮想アドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugSymbolProvider2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

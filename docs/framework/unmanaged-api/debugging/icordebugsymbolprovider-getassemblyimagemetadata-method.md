---
title: 'GetAssemblyImageMetadata Method Provider:: メソッド'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: fb08df3b594e0c34dfe4ca791983b0c111239b23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138912"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a>GetAssemblyImageMetadata Method Provider:: メソッド
マージされたアセンブリのメタデータを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppMemoryBuffer`  
 入出力マージされたアセンブリのメタデータのサイズとアドレスに関する情報を格納して[いる、のオブジェクトの](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)アドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugSymbolProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

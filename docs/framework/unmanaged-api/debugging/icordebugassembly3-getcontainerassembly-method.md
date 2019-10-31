---
title: ICorDebugAssembly3::GetContainerAssembly メソッド
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 39f8dd042ea785258dfe5c048ebc348852be6892
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095393"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly メソッド
この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppAssembly`  
 コンテナーアセンブリを表す、オブジェクトのアドレスへのポインター。メソッドの呼び出しが失敗した場合は**null** 。  
  
## <a name="return-value"></a>戻り値  
 メソッドの呼び出しが成功した場合は `S_OK`。それ以外の場合は、`S_FALSE`、`ppAssembly` は**null**になります。  
  
## <a name="remarks"></a>Remarks  
 このアセンブリが 1 つのコンテナー アセンブリ内の他のアセンブリとマージされている場合、このメソッドはコンテナー アセンブリを返します。 詳細と用語については、「 [ICorDebugProcess6:: EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) 」を参照してください。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugAssembly3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

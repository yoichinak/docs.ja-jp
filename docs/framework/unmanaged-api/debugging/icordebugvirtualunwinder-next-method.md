---
title: Icordebugvirtualunwinder::next メソッド
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74be827dc97213507b96da9e025923f859011acd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076888"
---
# <a name="icordebugvirtualunwindernext-method"></a>Icordebugvirtualunwinder::next メソッド
呼び出し元のコンテキストに進みます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next();  
```  
  
## <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` 正常にアンワインドが発生した場合または`CORDBG_S_AT_END_OF_STACK`フレームがあるため、アンワインドを完了できない場合。  
  
 失敗を示す HRESULT が返される場合、ICorDebug API は `CORDBG_E_DATA_TARGET_ERROR` を返します。  
  
## <a name="remarks"></a>Remarks  
 スタック ウォーカーにより、前へ進んでいることが確認されます。これにより、最終的に `Next` の呼び出しによって、失敗を示す HRESULT または `CORDBG_S_AT_END_OF_STACK` が返されます。 返す`S_OK`無期限に無限ループが発生する可能性があります。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMemoryBuffer インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

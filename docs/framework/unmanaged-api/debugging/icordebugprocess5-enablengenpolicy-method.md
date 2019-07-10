---
title: ICorDebugProcess5::EnableNGENPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38ff08fa7e7db986006c4e0e09b1ac9cf1be801e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767150"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy メソッド
アプリケーションがマネージ デバッガーで実行中にネイティブ イメージを読み込む方法を決定する値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ePolicy`  
 [in]A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)アプリケーションがマネージ デバッガーで実行中にネイティブ イメージを読み込む方法を決定する定数。  
  
## <a name="remarks"></a>Remarks  
 メソッドを返しますのかどうか、ポリシーが正常に設定されて、`S_OK`します。 場合`ePolicy`によって定義された列挙値の範囲外です[CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)、メソッドを返します`E_INVALIDARG`なり、メソッドの呼び出しに効力はありません。 ネイティブ イメージ ジェネレーター (Ngen.exe) のポリシーを更新できないかどうか、メソッドを返します`E_FAIL`します。  
  
 `ICorDebugProcess5::EnableNGenPolicy`メソッドは、プロセスの有効期間中にいつでも呼び出すことができます。 ポリシーは、有効なポリシーを設定した後に読み込まれたモジュールの。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

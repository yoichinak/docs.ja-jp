---
title: ICorDebugRuntimeUnwindableFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131886"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame インターフェイス
共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugRuntimeUnwindableFrame` は、テキストフレームインターフェイスの特殊なバージョンです。 これは、ランタイムが現在のスタック上のフレームをアンワインドする必要があるアンマネージメソッドによって使用されます。 既存のアンワインド規則は、JIT コンパイルコードを使用しないため、機能しません。 デバッガーに unwindable フレームが表示された場合、そのフレームをアンワインドするには、[次](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)のメソッドを使用する必要がありますが、検査自体を実行する必要があります。 デバッガーは、`ICorDebugRuntimeUnwindableFrame`を受信すると、テキストフレームのコンテキストを取得するために、「 [GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) 」メソッドを呼び出すことができます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

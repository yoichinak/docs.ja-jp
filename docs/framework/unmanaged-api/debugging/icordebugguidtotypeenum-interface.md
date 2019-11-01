---
title: ICorDebugGuidToTypeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138528"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum インターフェイス
整数のセットとそれに対応する型の間のマッピングを定義する列挙子を提供します。これは、テキストインスタンスによって表されます。 このインターフェイスは、ICorDebugEnum インターフェイスからメソッドを継承します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[いいね Totypeenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Guid を型情報にマップする、指定された数の[Cordebugguidtotypemapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)インスタンスを取得します。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugGuidToTypeEnum` インターフェイスオブジェクトは、 [ICorDebugAppDomain3:: GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッドを呼び出すことによって取得できます。 デバッガーは、このインターフェイスの[次](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)のメソッドを呼び出して、の 呼び出しに使用されるアプリケーションドメインに読み込まれた Windows ランタイム型のマネージ表現のマッピングを表す [cordebugguidtotypemapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) オブジェクトを取得できます。[ICorDebugAppDomain3:: GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッド。  
  
## <a name="requirements"></a>要件  
 **・** Windows ランタイム  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

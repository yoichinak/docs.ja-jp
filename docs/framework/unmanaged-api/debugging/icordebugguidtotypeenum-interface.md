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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025827"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum インターフェイス
一連の Guid とは、ICorDebugType のインスタンスによって表される、対応する型間のマッピングを定義する列挙子を提供します。 このインターフェイスは、ICorDebugEnum インターフェイスからメソッドを継承します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|指定した数を取得[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)インスタンス情報を入力する Guid にマップします。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugGuidToTypeEnum`インターフェイス オブジェクトを呼び出すことによって取得できます、 [icordebugappdomain 3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッド。 デバッガーは、このインターフェイスを呼び出すことができます[次](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)を取得するメソッド[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)で Windows ランタイム型のマネージ表現のマッピングを表すオブジェクトが読み込まれて、呼び出しに使用されるアプリケーション ドメイン、 [icordebugappdomain 3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** Windows ランタイム  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

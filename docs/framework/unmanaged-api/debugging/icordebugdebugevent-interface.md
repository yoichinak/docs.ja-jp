---
title: ICorDebugDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f838c9c2775023583b6879ea4c4a52727065114
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911266"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent インターフェイス
すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetEventKind メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|イベントが発生したスレッドを取得します。|  
  
## <a name="remarks"></a>Remarks  
 次のインターフェイスは、`ICorDebugDebugEvent` インターフェイスから派生したものです。  
  
- [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> このインターフェイスは .NET ネイティブでのみ使用可能です。 インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

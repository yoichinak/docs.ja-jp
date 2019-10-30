---
title: ICorDebugLoadedModule インターフェイス
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9fe36497844b9c33cefcf8c63711941196847525
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122610"
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule インターフェイス
読み込まれたモジュールについての情報を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBaseAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|読み込まれたモジュールのベース アドレスを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|読み込まれたモジュールの名前を取得します。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|読み込まれたモジュールのサイズ (バイト単位) を取得します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugLoadedModule` インターフェイスはデバッガーによって実装され、CLR デバッグ インターフェイスが、デバッガーから読み込まれたモジュールに関する情報を取得するために使用します。  
  
> [!NOTE]
> このインターフェイスは .NET ネイティブでのみ使用可能です。 .NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

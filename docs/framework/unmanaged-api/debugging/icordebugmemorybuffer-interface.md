---
title: ICorDebugMemoryBuffer インターフェイス
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 9e43f9a2297eb56755c7a6bba73e994441cbfeaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127974"
---
# <a name="icordebugmemorybuffer-interface"></a>ICorDebugMemoryBuffer インターフェイス
メモリ内のバッファーを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|メモリ バッファーのサイズ (バイト単位) を取得します。|  
|[GetStartAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|メモリ バッファーの開始アドレスを取得します。|  
  
## <a name="remarks"></a>Remarks  
  
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

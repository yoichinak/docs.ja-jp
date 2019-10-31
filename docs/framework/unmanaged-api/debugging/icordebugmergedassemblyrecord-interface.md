---
title: ICorDebugMergedAssemblyRecord インターフェイス
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 8dc07cb8c2f57ee6f9598c727cbd6de38bf4625f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139189"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord インターフェイス
マージされたアセンブリに関する情報を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCulture メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|アセンブリのカルチャ名文字列を取得します。|  
|[GetIndex メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|アセンブリのプレフィックス インデックスを取得します。|  
|[GetPublicKey メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|アセンブリの公開キーを取得します。|  
|[GetPublicKeyToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|アセンブリの公開キー トークンを取得します。|  
|[GetSimpleName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|アセンブリの簡易名を取得します。|  
|[GetVersion メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|アセンブリのバージョン情報を取得します。|  
  
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

---
title: ICorDebugCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca47eb5508907297a78dba1ab2b0a6d2b8ece0d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976929"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode インターフェイス

Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|指定したオフセット位置にブレークポイントを作成します。|  
|[GetAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|この `ICorDebugCode` が表すコード セグメントの RVA (Relative Virtual Address) を取得します。|  
|[GetCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。 このメソッドは非推奨とされました。使用して、 [icordebugcode 2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)代わりにします。|  
|[GetEnCRemapSequencePoints メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|実装されていません。|  
|[GetFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|これに関連付けられている"ICorDebugFunction"を取得します。`ICorDebugCode`します。|  
|[GetILToNativeMapping メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|MSIL オフセットからネイティブ オフセットへのマッピングを表す"COR_DEBUG_IL_TO_NATIVE_MAP"インスタンスの配列を取得します。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|この `ICorDebugCode` で表されるバイナリ コードのサイズ (バイト単位) を取得します。|  
|[GetVersionNumber メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|この `ICorDebugCode` が表すコードのバージョンを識別する、1 から始まる数字を取得します。|  
|[IsIL メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|この `ICorDebugCode` が MSIL でコンパイルされているかどうかを示す値を取得します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugCode` は、MSIL またはネイティブ コードを表すことができます。 MSIL コードを表す"ICorDebugFunction"オブジェクトは、0 個または 1 を持つことができます`ICorDebugCode`関連付けられているオブジェクト。 ネイティブ コードを表す"ICorDebugFunction"オブジェクトは、任意の数を持つことができます`ICorDebugCode`関連付けられているオブジェクト。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugCode3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

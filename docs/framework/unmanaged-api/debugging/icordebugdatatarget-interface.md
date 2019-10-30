---
title: ICorDebugDataTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: f8b216d370f7278f6d2a4beed5bab88afa666200
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122215"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget インターフェイス
特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPlatform メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|ターゲットプロセスが実行されているプラットフォーム (プロセッサアーキテクチャやオペレーティングシステムなど) に関する情報を提供します。|  
|[ReadVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|指定したアドレスを開始位置として連続したメモリのブロックを取得し、指定したバッファー内でそれを返します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|指定されたスレッドの現在のスレッドコンテキストを要求します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugDataTarget` とそのメソッドには、次の特性があります。  
  
- デバッグサービスは、このインターフェイスのメソッドを呼び出して、ターゲットプロセス内のメモリおよびその他のデータにアクセスします。  
  
- デバッガークライアントは、特定のターゲット (ライブプロセスやメモリダンプなど) に適した方法でこのインターフェイスを実装する必要があります。  
  
- `ICorDebugDataTarget` メソッドは、他の `ICorDebug*` インターフェイスに実装されているメソッド内からのみ呼び出すことができます。 これにより、デバッガークライアントは、呼び出されるスレッドとそのタイミングを制御できます。  
  
- `ICorDebugDataTarget` の実装は、常にターゲットに関する最新の情報を返す必要があります。  
  
 `ICorDebug*` インターフェイス (および `ICorDebugDataTarget` メソッド) が呼び出されている間は、ターゲットプロセスを停止し、変更することはできません。 ターゲットがライブプロセスであり、その状態が変更された場合、 [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)メソッドを再度呼び出して、置換されたののインスタンスを提供する必要があります。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

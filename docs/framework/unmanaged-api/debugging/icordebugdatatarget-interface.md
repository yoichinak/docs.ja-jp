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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989197"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget インターフェイス
特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPlatform メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|プロセッサ アーキテクチャと、ターゲット プロセスが実行されているオペレーティング システムを含む、プラットフォームについて説明します。|  
|[ReadVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|指定したアドレスから始まる連続したメモリのブロックを取得し、指定されたバッファーで返します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|指定したスレッドの現在のスレッド コンテキストを要求します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugDataTarget` そのメソッドに次の特性があります。  
  
- デバッグ サービスは、メモリと、ターゲット プロセスの他のデータにアクセスするには、このインターフェイスでメソッドを呼び出します。  
  
- デバッガー クライアントは、特定のターゲット (たとえば、ライブ プロセスまたはメモリ ダンプ) に適したには、このインターフェイスを実装する必要があります。  
  
- `ICorDebugDataTarget`メソッドは、他の実装されているメソッド内からのみ呼び出すことが`ICorDebug*`インターフェイス。 これにより、どのスレッドが呼び出されると、デバッガーのクライアントが制御すること。  
  
- `ICorDebugDataTarget`実装する必要があります、ターゲットに関する最新の情報を常に返します。  
  
 ターゲット プロセスを停止しているときに何らかの方法で変更されていない必要があります`ICorDebug*`インターフェイス (したがって`ICorDebugDataTarget`メソッド) が呼び出されます。 ターゲットがライブ プロセスとその状態の変更の場合、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)メソッドは、置換 ICorDebugProcess のインスタンスを指定してもう一度呼び出す必要があります。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

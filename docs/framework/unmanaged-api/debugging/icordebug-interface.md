---
title: ICorDebug インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193232ce1006a9cf209db9330343386404948440
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168286"
---
# <a name="icordebug-interface"></a>ICorDebug インターフェイス
開発者は、共通言語ランタイム (CLR) 環境でアプリケーションをデバッグできるようにするメソッドを提供します。  
  
> [!NOTE]
>  Windows 95、Windows 98、または Windows ME、または x86 以外のプラットフォーム (IA64、AMD64 など)、(マネージとネイティブ コード) を混合モード デバッグはサポートされていません。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanLaunchOrAttach メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|現在のコンピューターとランタイムの構成のコンテキスト内で、新しいプロセスの起動または特定のプロセスへのアタッチを実行するかどうかを判断します。|  
|[CreateProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|プロセスと、デバッガーの制御下で、プライマリ スレッドを起動します。|  
|[DebugActiveProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|既存のプロセスにデバッガーをアタッチします。|  
|[EnumerateProcesses メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|デバッグ中のプロセスの列挙子を取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|特定のプロセス ID を持つ"ICorDebugProcess"オブジェクトを返します|  
|[Initialize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|`ICorDebug` オブジェクトを初期化します。|  
|[SetManagedHandler メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|管理対象のイベントのイベント ハンドラー オブジェクトを指定します。|  
|[SetUnmanagedHandler メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|非管理対象のイベントのイベント ハンドラー オブジェクトを指定します。|  
|[Terminate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|終了、`ICorDebug`オブジェクト。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebug` デバッガー プロセスのイベント処理のループを表します。 デバッガーが待機する必要があります、 [icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)このインターフェイスを解放する前に、デバッグ中のすべてのプロセスからのコールバック。  
  
 `ICorDebug`オブジェクトは、初期のオブジェクトをさらに管理されているすべてのデバッグを制御します。 .NET Framework version 1.0 および 1.1 では、このオブジェクトは、 `CoClass` COM から作成されたオブジェクト .NET Framework version 2.0 では、このオブジェクトが不要になった、`CoClass`オブジェクト。 これで作成する必要があります、 [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)関数で、複数のバージョンに対応します。 この新しい作成機能により、クライアントはの特定の実装を取得する`ICorDebug`もに、デバッグ API の特定のバージョンをエミュレートします。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

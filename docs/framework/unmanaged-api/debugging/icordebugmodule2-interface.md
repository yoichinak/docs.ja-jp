---
title: ICorDebugModule2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: a3a1b658f4ab05c7029de907882fe5ab2513ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127883"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 インターフェイス

モジュールインターフェイスの論理拡張機能として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ApplyChanges メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|メタデータの変更と、Microsoft 中間言語 (MSIL) コードの変更を実行中のプロセスに適用します。|  
|[GetJITCompilerFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|この `ICorDebugModule2`の just-in-time (JIT) コンパイルを制御するフラグを取得します。|  
|[ResolveAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|指定したメタデータトークンによって参照されるアセンブリを解決します。|  
|[SetJITCompilerFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|この `ICorDebugModule2`の JIT コンパイルを制御するフラグを設定します。|  
|[SetJMCStatus メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|この `ICorDebugModule2` 内のすべてのクラスのすべてのメソッドのマイコードのみ (JMC) 状態を、指定した値に設定します。ただし、逆の値に設定するのは、`pTokens` 配列内のすべてのメソッドです。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

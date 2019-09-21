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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8fe1a25c4bc1f5e19f49f0d660d0aad5a180ea2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911889"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 インターフェイス

モジュールインターフェイスの論理拡張機能として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ApplyChanges メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|メタデータの変更と、Microsoft 中間言語 (MSIL) コードの変更を実行中のプロセスに適用します。|  
|[GetJITCompilerFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|この`ICorDebugModule2`の just-in-time (JIT) コンパイルを制御するフラグを取得します。|  
|[ResolveAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|指定したメタデータトークンによって参照されるアセンブリを解決します。|  
|[SetJITCompilerFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|この`ICorDebugModule2`の JIT コンパイルを制御するフラグを設定します。|  
|[SetJMCStatus メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|この`ICorDebugModule2`のすべてのクラスのすべてのメソッドのマイコードのみ (JMC) の状態を、指定した値に設定し`pTokens`ます。ただし、逆の値に設定されている配列内のすべてのメソッドを除きます。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

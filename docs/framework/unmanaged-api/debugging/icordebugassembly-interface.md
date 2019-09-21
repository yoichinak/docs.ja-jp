---
title: ICorDebugAssembly インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426269d14992ae0f1f8c02619b259cfdd4bcbf8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959439"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly インターフェイス

アセンブリを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateModules メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|アセンブリに格納されているモジュールの列挙子を取得します。|  
|[GetAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|この`ICorDebugAssembly`インスタンスを含むアプリケーションドメインへのインターフェイスポインターを取得します。|  
|[GetCodeBase メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|.NET Framework の現在のバージョンでは実装されていません。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|アセンブリの名前を取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|アセンブリが実行されている、のプロセスインスタンスを取得します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

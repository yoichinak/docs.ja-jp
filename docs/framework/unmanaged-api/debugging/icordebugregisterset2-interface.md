---
title: ICorDebugRegisterSet2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: 47beba867cd2246c98cb02c3a563b948c15f5154
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131314"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 インターフェイス
64を超えるレジスタを持つハードウェアプラットフォームに対し[て、の](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)機能を拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRegisters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。|  
|[GetRegistersAvailable メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|使用できるレジスタのビットマップを提供するバイト配列を取得します。|  
|[SetRegisters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|.NET Framework バージョン2.0 では実装されていません。|  
  
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
- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

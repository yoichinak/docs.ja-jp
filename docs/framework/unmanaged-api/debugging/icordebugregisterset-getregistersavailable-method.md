---
title: ICorDebugRegisterSet::GetRegistersAvailable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f341098268f735a576bdbc5f0cea52f1a7e14f90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782902"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable メソッド
これで登録することを示す取得がビット マスク[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)現在利用します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAvailable`  
 [out]どのレジスタが現在の使用を示すビット マスクです。  
  
## <a name="remarks"></a>Remarks  
 レジスタは、その値は、特定の状況を特定できない場合に使用できない可能性があります。  
  
 返されたマスクには、各レジスタのビットが含まれています (1 << レジスタのインデックス)。 登録がある場合は、ビット値が 1 または 0 が使用できない場合。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

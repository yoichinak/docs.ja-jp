---
title: ICorDebugRegisterSet::SetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: 7af3109c822dfe945a60c16d4bd3b764f7550492
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131340"
---
# <a name="icordebugregistersetsetregisters-method"></a>ICorDebugRegisterSet::SetRegisters メソッド
`SetRegisters` は .NET Framework バージョン2.0 では実装されていません。 このメソッドを呼び出さないでください。  
  
> [!NOTE]
> 「いいね!: [: setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) 」や「いいね!: [: setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)」などの上位レベルの操作を使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

---
title: ICorDebugRegisterSet::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: debb704900d852df1d66c7bac65ab385e0d72ec5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769945"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a>ICorDebugRegisterSet::SetThreadContext メソッド
`SetThreadContext` .NET Framework version 2.0 では実装されていません。 このメソッドを呼び出さないでください。  
  
> [!NOTE]
>  高度な操作を使用して[icordebugnativeframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)スレッドのコンテキストを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1, 1.0  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

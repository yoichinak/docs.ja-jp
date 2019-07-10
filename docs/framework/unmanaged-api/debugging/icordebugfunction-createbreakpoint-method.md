---
title: ICorDebugFunction::CreateBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6eb93b84baf9dcd82d89bb1a4711a91d97c52779
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754794"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a>ICorDebugFunction::CreateBreakpoint メソッド
この関数の先頭にブレークポイントを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppBreakpoint`  
 [out]関数の新しいブレークポイントを表す ICorDebugFunctionBreakpoint オブジェクトのアドレスへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

---
title: ICorDebugModule::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff7c77a27e9be58e9702c3a5e3f990863dc83901
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763627"
---
# <a name="icordebugmodulegetprocess-method"></a>ICorDebugModule::GetProcess メソッド
このモジュールを格納しているプロセスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppProcess`  
 [out]このモジュールを格納しているプロセスを表す ICorDebugProcess オブジェクトのアドレスへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

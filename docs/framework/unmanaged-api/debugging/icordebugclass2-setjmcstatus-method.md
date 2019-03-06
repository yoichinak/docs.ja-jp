---
title: ICorDebugClass2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed6570e11008e52d4b1f97c2dc90e2ccbef2e35
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471382"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus メソッド
クラスの各メソッドでは、メソッドは、ユーザー定義のコードかどうかを示す値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bIsJustMyCode`  
 [in]設定`true`メソッドがユーザー定義であることを示すコードは、それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 マイ コード (のみ JMC) のステッパでは、非ユーザー定義のコードをスキップします。 ユーザー定義のコードは、デバッグできるコードのサブセットである必要があります。  
  
 `SetJMCStatus` 場合でも、その他のすべてのメソッドの値を正常に設定、任意のメソッドの値の設定に失敗した場合は、S_FALSE の HRESULT 値を返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

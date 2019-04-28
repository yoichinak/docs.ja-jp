---
title: ICorDebugFunction2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49ced1b4be888c7550c3927d1b319ab2f0bef086
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763777"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus メソッド
マイ コードのみのこの ICorDebugFunction2 によって表される関数をマーク ステップ実行します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bIsJustMyCode`  
 [in]設定`true`ユーザー コードとして関数をマークする場合は、`false`します。  
  
## <a name="return-values"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|関数は正しく設定されました。|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|デバッグすることはできませんので、関数をユーザー コードとしてマークされませんでした。|  
  
## <a name="remarks"></a>Remarks  
 マイ コードのみステッパでは、非ユーザー コードをスキップします。 ユーザー コードは、デバッグできるコードのサブセットである必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

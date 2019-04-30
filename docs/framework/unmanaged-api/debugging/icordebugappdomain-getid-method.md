---
title: ICorDebugAppDomain::GetId メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0aefc19ca0c255c9c8ea40fcc12fc5cba1b00f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996256"
---
# <a name="icordebugappdomaingetid-method"></a>ICorDebugAppDomain::GetId メソッド
アプリケーション ドメインの一意の識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pId`  
 [out]アプリケーション ドメインの一意の識別子。  
  
## <a name="remarks"></a>Remarks  
 アプリケーション ドメインの識別子は、格納しているプロセス内で一意です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

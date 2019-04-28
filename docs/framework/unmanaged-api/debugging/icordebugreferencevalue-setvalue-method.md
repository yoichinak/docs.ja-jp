---
title: ICorDebugReferenceValue::SetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59ef7bf8f17e79c9ae7b80dd314a5afce7fa9584
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782942"
---
# <a name="icordebugreferencevaluesetvalue-method"></a>ICorDebugReferenceValue::SetValue メソッド
指定されたメモリ アドレスを設定します。 つまり、このメソッドは、オブジェクトを指すためにこの ICorDebugReferenceValue を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `value`  
 [in]A`CORDB_ADDRESS`このオブジェクトのアドレスを指定する値`ICorDebugReferenceValue`ポイント。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

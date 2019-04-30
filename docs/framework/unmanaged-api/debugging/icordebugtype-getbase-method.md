---
title: ICorDebugType::GetBase メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d04bc67013a2227f295ac3a41be027b9f9b04e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946311"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase メソッド
1 つが存在する場合、これによって表される型の基本の型を表す、ICorDebugType へのインターフェイス ポインターを取得`ICorDebugType`します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pBase`  
 [out]アドレスへのポインター、`ICorDebugType`基本データ型を表すオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 型の基本型の検索は、オブジェクトまたはその親クラスのすべてのフィールドの印刷などの一般的なデバッガー機能を実装するために便利です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

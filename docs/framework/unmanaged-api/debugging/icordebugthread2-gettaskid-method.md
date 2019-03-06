---
title: ICorDebugThread2::GetTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 417f99c2b9fa7e77f8696c27cb3929c92956c08c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494650"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID メソッド
このスレッドで実行されているタスクの識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pTaskId`  
 [out]この ICorDebugThread2 オブジェクトによって表されるスレッドで実行中のタスクの識別子へのポインター。  
  
## <a name="remarks"></a>Remarks  
 スレッドが、接続に関連付けられた場合、タスクはのみ、スレッドで実行できます。 `GetTaskID` 0 が返されます`pTaskId`スレッドは、接続に関連付けられていない場合。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

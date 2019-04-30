---
title: ICorDebugEval::NewString メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db609bdee7975b6c067271f99529e2cf2240f720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989028"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString メソッド
指定した内容を含む新しい文字列インスタンスを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `string`  
 [in]文字列の内容へのポインター。  
  
## <a name="remarks"></a>Remarks  
 文字列が現在のスレッドが実行されているアプリケーション ドメインで常に作成されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

---
title: IDebugAutoAttach::AutoAttach メソッド
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16ccc56579a1ebe45ada61a9565cc8ade335333d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469679"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach メソッド
サーバー起動デバッガーの自動実行をアタッチします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `guidPort`  
 [in]常に設定`GUID_NULL`します。  
  
 `dwPid`  
 [in]プロセス ID で通常取得、`GetCurrentProcessId`関数。  
  
 `dwProgramType`  
 [in]プログラムの種類: `AUTOATTACH_PROGRAM_WIN32`、 `AUTOATTACH_PROGRAM_COMPLUS`、または`AUTOATTACH_PROGRAM_UNKNOWN`します。  
  
 `dwProgramId`  
 [in]プログラム id。  
  
 `pszSessionId`  
 [in]Debug 動詞によって渡された文字列。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** DbgAutoAttach.h  
  
## <a name="see-also"></a>関連項目
- [IDebugAutoAttach インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)

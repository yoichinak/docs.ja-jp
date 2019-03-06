---
title: ICorDebugCode::CreateBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df27d2ab609551bb7a7f6f4b0ff8c7118c9f93f8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478675"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint メソッド
指定したオフセットには、このコード セグメントでは、ブレークポイントを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `offset`  
 [in]ブレークポイントを作成するオフセットです。  
  
 `ppBreakpoint`  
 [out]ブレークポイントを表す"ICorDebugFunctionBreakpoint"オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 前に、ブレークポイントがアクティブでは、プロセス オブジェクトに追加する必要があります。  
  
 このコードは、Microsoft intermediate language (MSIL) コードでは、およびの just-in-time (JIT) があるかどうか、コードの JIT コンパイルにも、ブレークポイント、コードのコンパイル済みのネイティブのバージョンが適用されます。 (同じは、コードが JIT コンパイルされた後では、true を返します。)  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目


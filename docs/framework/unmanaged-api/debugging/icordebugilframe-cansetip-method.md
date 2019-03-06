---
title: ICorDebugILFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49cef22e88613fe4c4dfb3fb35a92977977b1827
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473566"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP メソッド
命令ポインターを Microsoft 中間言語 (MSIL) コードで指定されたオフセット位置に設定しても安全でかどうかを示す HRESULT を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `nOffset`  
 [in]命令ポインターの必要な設定です。  
  
## <a name="remarks"></a>Remarks  
 使用して、`CanSetIP`メソッドを呼び出す前に、 [icordebugilframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)メソッド。 場合`CanSetIP`HRESULT を返します、S_OK 以外を呼び出すことができますも`ICorDebugILFrame::SetIP`デバッガーがデバッグ中のコードの安全かつ適切な実行を継続するという保証はありません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl, CorDebug,h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

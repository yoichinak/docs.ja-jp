---
title: ICorDebugNativeFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cac53ba77f04141d8d36b270226e97c292399eb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482731"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP メソッド
ネイティブ コードのオフセット命令ポインターが現在設定されている場所を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pnOffset`  
 [out]ネイティブ コード内のオフセット位置へのポインター。  
  
## <a name="remarks"></a>Remarks  
 この"ICorDebugNativeFrame"で表されるスタック フレームがアクティブな場合は、オフセットは、実行する次の命令のアドレスです。 このスタック フレームがアクティブでない場合、オフセットは、次のスタック フレームが再アクティブ化時に実行される命令のアドレスです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目


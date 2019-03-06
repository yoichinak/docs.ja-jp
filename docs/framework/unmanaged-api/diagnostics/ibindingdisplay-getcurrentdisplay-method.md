---
title: IBindingDisplay::GetCurrentDisplay メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f9cc44db9c93a8b018d0586bc1faeda7cfbc9bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498433"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>IBindingDisplay::GetCurrentDisplay メソッド
現在のバインディングの表示情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `display`  
 [out, retval]バインドの表示情報を含む safearray へのポインター。  
  
## <a name="remarks"></a>Remarks  
 [Ibindingdisplay::initializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)メソッドが以前に成功しましたが、デバッガーでプログラムを停止する必要があります。  
  
 呼び出し元の返される割り当てを解除する必要があります`SAFEARRAY`を使用してメモリ[SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** BindingDisplay.h  
  
 **ライブラリ:** BindingDisplay.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IBindingDisplay インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [InitializeForProcess メソッド](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)

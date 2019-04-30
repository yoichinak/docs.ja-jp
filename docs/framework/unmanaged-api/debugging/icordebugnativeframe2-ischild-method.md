---
title: ICorDebugNativeFrame2::IsChild メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9503c12da9e98fbd43f3904aad25c5d10655cec2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994644"
---
# <a name="icordebugnativeframe2ischild-method"></a>ICorDebugNativeFrame2::IsChild メソッド
現在のフレームが子フレームであるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pIsChild`  
 [out]現在のフレームが子フレームであるかどうかを指定するブール値。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|子の状態が正常に返されました。|  
|E_FAIL|子の状態が返されませんでした。|  
|E_INVALIDARG|`pIsChild` が null です。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 `IsChild`メソッドを返します。`true`フレーム オブジェクトを、メソッドを呼び出すことが別のフレームの子である場合。 大文字と小文字の場合を使用して、 [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)フレームを親となっているかどうかを確認する方法。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugNativeFrame2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugILFrame2::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7454b551edc546fecbd9d091f7c821e0a07b16df
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497822"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters メソッド
含む ICorDebugTypeEnum オブジェクトを取得、<xref:System.Type>このフレーム内のパラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppTyParEnum`  
 型パラメーターの列挙を許可する ICorDebugTypeEnum インターフェイス オブジェクトのアドレスへのポインター。  
  
 型パラメーターの一覧には、メソッドの型パラメーター (ある場合) 後にクラス型パラメーター (ある場合) が含まれます。  
  
## <a name="remarks"></a>Remarks  
 使用して、 [imetadataimport 2::enumgenericparams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)をクラスの型パラメーターとメソッドの数の入力パラメーターがこの一覧が含まれています。  
  
 型パラメーターは、常に使用できません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

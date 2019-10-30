---
title: ICorPublishAppDomain::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140355"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName メソッド
この[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)によって表されるアプリケーションドメインの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cchName`  
 [in] `szName` 配列のサイズ。  
  
 `pcchName`  
 入出力`szName` 配列に返された、null 文字を含むワイド文字の数へのポインター。  
  
 `szName`  
 入出力名前を格納する配列。  
  
## <a name="remarks"></a>Remarks  
 `szName` が null 以外の場合、`GetName` メソッドは `szName`に最大 `cchName` 文字 (null ターミネータを含む) をコピーします。 `pcchName`で null 以外の値が返された場合、名前の実際の文字数 (null ターミネータを含む) が `szName` 配列に格納されます。  
  
 `GetName` メソッドは、コピーされた文字数に関係なく S_OK HRESULT を返します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublishAppDomain インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)

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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178416"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName メソッド
この[ICorPublishAppDomain](icorpublishappdomain-interface.md)によって表されるアプリケーション ドメインの名前を取得します。  
  
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
 [アウト]配列に返される null 文字を含むワイド文字の数への`szName`ポインター。  
  
 `szName`  
 [アウト]名前を格納する配列。  
  
## <a name="remarks"></a>解説  
 null`szName`以外の場合、`GetName`メソッドは最大`cchName`文字 (null 終端文字を含む)`szName`を にコピーします。 で null 以外が返される`pcchName`場合、名前の実際の文字数 (NULL 終端文字を含む) が`szName`配列に格納されます。  
  
 この`GetName`メソッドは、コピーされた文字数に関係なく、hRESULT S_OKを返します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コルパブ.idl,コルパブ.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublishAppDomain インターフェイス](icorpublishappdomain-interface.md)

---
title: ISymUnmanagedBinder::GetReaderFromStream メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 630895e131c2b3fd5a175a7a3c45140ad65d03aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503035"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>ISymUnmanagedBinder::GetReaderFromStream メソッド
メタデータ インターフェイスとシンボル ストアを格納しているストリームでは、指定されたを返します、正しい[ISymUnmanagedReader](isymunmanagedreader-interface.md)構造は、デバッグを読み取ることが特定のシンボル ストアからシンボルします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  
 `importer`  
 [in]メタデータ インポート インターフェイスへのポインター。  
  
 `pstream`  
 [in]シンボル ストアを格納しているストリームへのポインター。  
  
 `pRetVal`  
 [out]設定されているポインターに返された[ISymUnmanagedReader](isymunmanagedreader-interface.md)インターフェイス。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目
- [ISymUnmanagedBinder インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)

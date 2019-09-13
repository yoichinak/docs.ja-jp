---
title: ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a54d3cb1bb9abf740c2c9b5a9a8312a9612ae658
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894457"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a>ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド
1つのグローバル変数を定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 からグローバル変数名。  
  
 `attributes`  
 からグローバル変数属性。  
  
 `sigToken`  
 から署名のメタデータトークン。  
  
 `addrKind`  
 からアドレスの種類。  
  
 `addr1`  
 からパラメーター指定の最初のアドレス。  
  
 `addr2`  
 からパラメーター指定の2番目のアドレス。  
  
 `addr3`  
 からパラメーター指定の3番目のアドレス。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK を返します。それ以外の場合は E_FAIL またはその他のエラーコードを返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym .idl  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineGlobalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)

---
title: ISymUnmanagedWriter::DefineLocalVariable メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c561eb70f0e3d243984decfb39629601f8eeea37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125299"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable メソッド
現在の構文のスコープの変数を 1 つ定義します。 このメソッドをスコープ全体で複数のホームのある同じ名前の変数を複数回呼び出すことができます。 この場合、ただしの値、`startOffset`と`endOffset`パラメーターが重複しない必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 [in]ポインター、`WCHAR`ローカル変数の名前を定義します。  
  
 `attributes`  
 [in]ローカル変数の属性。  
  
 `cSig`  
 [in]A`ULONG32`のサイズ (バイト単位) を示す、`signature`バッファー。  
  
 `signature`  
 [in]ローカル変数シグネチャ。  
  
 `addrKind`  
 [in]アドレスの種類。  
  
 `addr1`  
 [in]パラメーター指定の最初のアドレス。  
  
 `addr2`  
 [in]パラメーター指定の 2 番目のアドレス。  
  
 `addr3`  
 [in]パラメーター指定の 3 番目のアドレス。  
  
 `startOffset`  
 [in]変数の開始オフセット。 このパラメーターは省略できます。 0 の場合は、このパラメーターは無視され、スコープ全体で変数が定義されています。 0 以外の値の場合は、現在のスコープのオフセット内、変数となります。  
  
 `endOffset`  
 [in]変数の終了オフセット。 このパラメーターは省略できます。 0 の場合は、このパラメーターは無視され、スコープ全体で変数が定義されています。 0 以外の値の場合は、現在のスコープのオフセット内、変数となります。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineGlobalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)

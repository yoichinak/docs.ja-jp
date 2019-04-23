---
title: ISymUnmanagedWriter2::DefineLocalVariable2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2caa9b48fc92a1b2e82f574d37d99758e19382c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133199"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 メソッド
現在の構文のスコープの変数を 1 つ定義します。 このメソッドをスコープ全体で複数のホームのある同じ名前の変数を複数回呼び出すことができます。 この場合、ただしの値、`startOffset`と`endOffset`パラメーターが重複しない必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 [in]ローカル変数の名前。  
  
 `attributes`  
 [in]ローカル変数の属性。  
  
 `sigToken`  
 [in]シグネチャのメタデータ トークンです。  
  
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
 **ヘッダー:** CorSym.idl  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)

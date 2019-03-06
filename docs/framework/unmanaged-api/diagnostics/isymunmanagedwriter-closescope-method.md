---
title: ISymUnmanagedWriter::CloseScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 250e58e4153edbee5c327ad46ecde73e94b83584
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468716"
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope メソッド
現在の構文のスコープを閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a>パラメーター  
 `endOffset`  
 [in] \(バイト単位\) の構文のスコープ内の最後の命令の最後のポイントのメソッドの先頭からのオフセット。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="remarks"></a>コメント  
 スコープを終了すると、その中は変数を定義できます。  
  
 [Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)で使用できる非透過スコープ識別子を返します[isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)を後で、スコープを定義の開始位置と終了オフセット。 この場合、`ISymUnmanagedWriter::OpenScope` と `ISymUnmanagedWriter::CloseScope` に渡したオフセットは無視されます。 スコープ識別子は、現在のメソッドでのみ有効です。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目
- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

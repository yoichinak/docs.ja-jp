---
title: ISymUnmanagedWriter::Abort メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 090183cad17aff6faf5e79639eadff086c1a26ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119536"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort メソッド
シンボルをシンボル ストアにコミットせずには、シンボル ライターを閉じます。 この呼び出しの後、シンボルのライターが、以降の更新は無効になります。 コミットのシンボルをシンボル ライターを閉じるは、使用、 [isymunmanagedwriter::close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

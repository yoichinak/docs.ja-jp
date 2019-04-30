---
title: ISymUnmanagedWriter::OpenScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ea6ce91e0651e09fb908d8b8b35811349ac8845
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986038"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope メソッド
現在のメソッドの構文の新しいスコープを開きます。 スコープは、新しい現在のスコープになり、スコープのスタックにプッシュされます。 スコープは、階層を形成する必要があります。 兄弟は、重複は許可されません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  
 `startOffset`  
 [in]メソッドの先頭からのバイト単位での構文のスコープ内の最初の命令のオフセット。  
  
 `pRetVal`  
 [out]ポインターを`ULONG32`スコープ識別子を受け取る。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="remarks"></a>Remarks  
 `ISymUnmanagedWriter::OpenScope` 使用できる非透過スコープ識別子を返します[isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)スコープを定義するの開始位置と終了後にオフセットします。 この場合に渡したオフセット`ISymUnmanagedWriter::OpenScope`と[isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)は無視されます。 スコープ識別子は、現在のメソッドでのみ有効です。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

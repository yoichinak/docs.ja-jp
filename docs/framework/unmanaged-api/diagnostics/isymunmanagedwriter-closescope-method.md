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
ms.openlocfilehash: 4d8790dc68bc063deed4c58ba0df8e9ea258b9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610081"
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope メソッド
現在の構文のスコープを閉じます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a>パラメーター  
 `endOffset`  
 から構文のスコープの最後の命令の末尾にある点の、メソッドの先頭からのオフセット (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="remarks"></a>解説  
 スコープを閉じた後は、それ以上の変数を定義することはできません。  
  
 [ISymUnmanagedWriter:: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)は、 [ISymUnmanagedWriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md)と共に使用してスコープの開始オフセットと終了オフセットを後で定義できる、不透明なスコープ識別子を返します。 この場合、`ISymUnmanagedWriter::OpenScope` と `ISymUnmanagedWriter::CloseScope` に渡したオフセットは無視されます。 スコープ識別子は、現在のメソッドでのみ有効です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)

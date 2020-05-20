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
ms.openlocfilehash: 4008b2a7d785781da5f35b3dc1e564487cb8e760
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609782"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope メソッド
現在のメソッドの構文の新しいスコープを開きます。 スコープは新しい現在のスコープになり、スコープのスタックにプッシュされます。 スコープは階層を形成する必要があります。 兄弟を重ねることはできません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  
 `startOffset`  
 からメソッドの先頭からの、構文のスコープの最初の命令のオフセット (バイト単位)。  
  
 `pRetVal`  
 入出力スコープ識別子を受け取るへのポインター `ULONG32` 。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="remarks"></a>解説  
 `ISymUnmanagedWriter::OpenScope`スコープの開始オフセットと終了オフセットを後で定義するために[ISymUnmanagedWriter:: SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)と共に使用できる非透過スコープ識別子を返します。 この場合、 `ISymUnmanagedWriter::OpenScope` と[ISymUnmanagedWriter:: cloに](isymunmanagedwriter-closescope-method.md)渡されるオフセットは無視されます。 スコープ識別子は、現在のメソッドでのみ有効です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)

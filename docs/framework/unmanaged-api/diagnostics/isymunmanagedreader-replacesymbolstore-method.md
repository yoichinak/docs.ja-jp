---
title: ISymUnmanagedReader::ReplaceSymbolStore メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8721f7c30061fbfd4a761bed090b761762c3c13c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939016"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore メソッド
既存のシンボル ストアをデルタ シンボル ストアで置き換えます。 このメソッドは、指定されたデルタが更新ではなく完全な置換として機能する点を除いて、"更新プログラム"[ストア](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)メソッドに似ています。  
  
> [!NOTE]
> `filename`またはパラメーターのいずれか1つ`pIStream`だけを指定する必要があります。両方を指定することはできません。 を`filename`指定した場合、シンボルストアはそのファイル内のシンボルで更新されます。 を`pIStream`指定した場合、ストアは<xref:System.Runtime.InteropServices.ComTypes.IStream>からのデータで更新されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>パラメーター  
 `filename`  
 からシンボルストアを格納しているファイルの名前。  
  
 `pIStream`  
 からパラメーターの`filename`代わりに使用されるファイルストリーム。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK を返します。それ以外の場合は E_FAIL またはその他のエラーコードを返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedReader インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

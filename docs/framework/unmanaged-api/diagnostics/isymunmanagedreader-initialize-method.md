---
title: ISymUnmanagedReader::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2dceeb2f0b3aa9f3147157e77087dffbf2d5f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939032"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize メソッド
このリーダーが関連付けられるメタデータインポーターインターフェイスと、モジュールのファイル名を使用して、シンボルリーダーを初期化します。  
  
> [!NOTE]
> このメソッドを呼び出すことができるのは1回だけです。他のリーダーメソッドの前に呼び出す必要があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>パラメーター  
 `importer`  
 からこのリーダーが関連付けられるメタデータインポーターインターフェイス。  
  
 `filename`  
 からモジュールのファイル名。 代わりに、 `pIStream`パラメーターを使用できます。  
  
 `searchPath`  
 から検索するパス。 このパラメーターは省略できます。  
  
 `pIStream`  
 からファイルストリーム。 filename パラメーターの代わりに使用されます。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK を返します。それ以外の場合は E_FAIL またはその他のエラーコードを返します。  
  
## <a name="remarks"></a>Remarks  
 または`filename`パラメーターのいずれか1つだけを指定する必要があります。両方を指定することはできません。 `pIStream` `searchPath` パラメーターは省略可能です。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedReader インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

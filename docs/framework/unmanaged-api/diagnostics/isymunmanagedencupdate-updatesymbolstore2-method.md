---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a4bcc4e6994f06fabf69e5548ad6922343b7dd5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479793"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 メソッド
コンパイラが行情報が要件を満たしている限り、プログラム データベース (PDB) のストリームから変更されていない関数を省略できるようにします。 PDB の行の古い情報と、関数のすべての行の 1 つのデルタは正しい行情報を確認できます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pIStream`  
 [in]ポインター、 [IStream](/windows/desktop/api/objidl/nn-objidl-istream)行情報を格納します。  
  
 `pDeltaLines`  
 [in]ポインターを[SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md)が変更された行を含む構造体。  
  
 `cDeltaLines`  
 [in]A`ULONG`が変更された行の数を表します。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目
- [ISymUnmanagedENCUpdate インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

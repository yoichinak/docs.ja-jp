---
title: ISymUnmanagedBinder3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfd8e8fc419809a3a490639ada1c533f286fe8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157509"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 インターフェイス
シンボル バインダー インターフェイスを拡張します。 このインターフェイスを呼び出すことによって取得`QueryInterface`を実装するオブジェクトで、`ISymUnmanagedBinder`インターフェイス。  
  
> [!IMPORTANT]
>  信頼できないソースからプログラム データベース (PDB) ファイルをセキュリティ リスクになります。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReaderFromCallback メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|ユーザーに実装するか、コールバックを使用して指定できるように、`IID_IDiaReadExeAtRVACallback`または`IID_IDiaReadExeAtOffsetCallback`メモリからデバッグ ディレクトリ情報を取得するには|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)

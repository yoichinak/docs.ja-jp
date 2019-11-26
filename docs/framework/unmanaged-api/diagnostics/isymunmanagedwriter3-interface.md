---
title: ISymUnmanagedWriter3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 115d4b58b01606c29719fb88ab7dbf5a858b1251
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438171"
---
# <a name="isymunmanagedwriter3-interface"></a>ISymUnmanagedWriter3 インターフェイス
Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables. This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Commit メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|Commits the changes written so far to the stream.|  
|[OpenMethod2 メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|Opens a method and provides its real section offset in the image.|  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)

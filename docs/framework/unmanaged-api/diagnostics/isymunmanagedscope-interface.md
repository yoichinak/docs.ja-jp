---
title: ISymUnmanagedScope インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446265"
---
# <a name="isymunmanagedscope-interface"></a>ISymUnmanagedScope インターフェイス
Represents a lexical scope within a method.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetChildren メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|Gets the children of this scope.|  
|[GetEndOffSet メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|Gets the end offset for this scope.|  
|[GetLocalCount メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|Gets a count of the local variables defined within this scope.|  
|[GetLocals メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|Gets the local variables defined within this scope.|  
|[GetMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|Gets the method that contains this scope.|  
|[GetNamespaces メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|Gets the namespaces that are being used within this scope.|  
|[GetParent メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|Gets the parent scope of this scope.|  
|[GetStartOffSet メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|Gets the start offset for this scope.|  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

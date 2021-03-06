---
title: "ISymUnmanagedScope2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2
helpviewer_keywords: ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d2ec846a34b2d3424f7bf8b54f1d4d12d4102e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 インターフェイス
メソッド内での構文のスコープを表します。 このインターフェイスは、 [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)スコープ内で定義されている定数に関する情報を取得するメソッドを持つインターフェイスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetConstantCount メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|このスコープ内で定義されている定数の数を取得します。|  
|[GetConstants メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|このスコープ内で定義されているローカル定数を取得します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>参照  
 [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedScope インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

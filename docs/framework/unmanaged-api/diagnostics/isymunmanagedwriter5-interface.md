---
title: ISymUnmanagedWriter5 インターフェイス
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6ed8c6e61c558a4bc9e3f92d559615ac93ecff8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144236"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 インターフェイス
ISymUnmanagedWriter5 インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスには、次のメソッドが含まれています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|マッピングの情報ソースへのトークンの範囲は、特別なカスタム データのセクションを閉じます。 閉じられた後は、以上のマッピング情報を追加できます。|  
|[MapTokenToSourceSpan メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|指定したソース ファイルで指定されたソース行に指定したメタデータ トークン span をマップします。<br /><br /> 呼び出しの間で呼び出す必要がある[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)します。|  
|[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|マップする span ソースへのトークン情報を出力するカスタム データの特別なセクションを開きます。 メソッドがまだ開いてまたはその逆の場合、エラーには、このセクションを開くことです。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)

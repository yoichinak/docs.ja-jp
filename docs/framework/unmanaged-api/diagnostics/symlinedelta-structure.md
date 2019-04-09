---
title: SYMLINEDELTA 構造体
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159485"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA 構造体
編集の結果として移動されたメソッドに関する情報をシンボル ハンドラーを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`mdMethod`|メソッドのメタデータ トークンです。|  
|`delta`|メソッドが移動された行の数。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断構造体](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)

---
title: IMethodMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077785"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc インターフェイス
新しい Microsoft intermediate language (MSIL) 関数本体にメモリを割り当てるメソッドを提供します。  
  
> [!NOTE]
>  `IMethodMalloc`インターフェイスは、単純なメモリ アロケーター。 これにより、メモリを割り当て、解放することができます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Alloc メソッド](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|新しい MSIL 関数本体の指定された量のメモリを割り当てようとします。|  
  
## <a name="remarks"></a>Remarks  
 各アロケーター モジュールに固有であり、関数本体は、モジュールのベースから正の値のオフセット位置になります。 モジュールのベースを超えるメモリはアロケーター関数本体にのみメモリを割り当てに使用するため貴重なことができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

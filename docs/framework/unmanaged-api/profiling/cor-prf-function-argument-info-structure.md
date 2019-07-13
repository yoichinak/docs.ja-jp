---
title: COR_PRF_FUNCTION_ARGUMENT_INFO 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 658b88349bedcbcefd0b97226c7bd1fa34f656c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781923"
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO 構造体
関数の引数を左から右方向で表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`numRanges`|引数のブロックの数。 これは、この値が、数ある[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)内の構造体、`ranges`配列。|  
|`totalArgumentSize`|すべての引数の合計サイズ。 つまり、この値は、引数の長さの合計です。|  
|`ranges`|配列の`COR_PRF_FUNCTION_ARGUMENT_RANGE`構造体、関数の引数の 1 つのブロックのそれぞれ表します。|  
  
## <a name="remarks"></a>Remarks  
 関数は、多くの引数があります。 これらの引数は可能性がありますメモリ内で連続して格納されません。 3 つの引数を 1 か所でのブロック、別の場所に 2 つの引数のブロック、および別の場所に 1 つの引数の最後のブロックするがあります。 これらの引数はすべて、同じ関数のさまざまな場所にだけ格納されます。  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO`構造体が 1 つの関数のすべての引数を表します。 関数の引数のすべてのブロックを参照するのに配列を使用します。 そのために、1 つのある 1 つの関数`COR_PRF_FUNCTION_ARGUMENT_INFO`構造体は、複数の参照`COR_PRF_FUNCTION_ARGUMENT_RANGE`構造体、1 つまたは複数の関数の引数を参照します。  
  
 レジスタに格納されている引数は、構造を構築するメモリに書き込まれました。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

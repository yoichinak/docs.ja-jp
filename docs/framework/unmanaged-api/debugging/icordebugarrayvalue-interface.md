---
title: ICorDebugArrayValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99bd3e9ae1faec1b71933681fadf4816b4789c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952211"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue インターフェイス

1次元配列または多次元配列を表す、値のサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBaseIndicies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|配列内の各次元のベースインデックスを取得します。|  
|[GetCount メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|配列内の要素の合計数を取得します。|  
|[GetDimensions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|配列の次元を取得します。|  
|[GetElement メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|配列内の指定された要素を表す値を取得します。|  
|[GetElementAtPosition メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|配列を0から始まる1次元配列として扱い、指定された位置にある要素を取得します。|  
|[GetElementType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|配列内の要素の単純型を取得します。|  
|[GetRank メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|配列のディメンションの数を取得します。|  
|[HasBaseIndicies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|配列にベースインデックスがあるかどうかを判断します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugArrayValue`では、1次元配列と多次元配列の両方がサポートされています。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

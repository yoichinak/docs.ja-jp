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
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168390"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue インターフェイス

1 次元または多次元配列を表すのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBaseIndicies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|配列内の各次元のベース インデックスを取得します。|  
|[GetCount メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|配列の要素の合計数を取得します。|  
|[GetDimensions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|配列の次元を取得します。|  
|[GetElement メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|配列内の指定した要素を表す値を取得します。|  
|[GetElementAtPosition メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|0 から始まる 1 次元の配列として、配列を扱う方法の指定された位置に要素を取得します。|  
|[GetElementType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|配列内の要素の単純な型を取得します。|  
|[GetRank メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|配列のディメンションの数を取得します。|  
|[HasBaseIndicies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|配列のベース インデックスがあるかどうかを判断します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugArrayValue` 1 次元配列と多次元の両方の配列をサポートしています。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

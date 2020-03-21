---
title: VariableLocationType 列挙型
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178357"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType 列挙型
変数のネイティブな場所の型を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`VLT_REGISTER`|変数はレジスタにあります。|  
|`VLT_REGISTER_RELATIVE`|変数はレジスタ相対メモリ位置にあります。|  
|`VLT_INVALID`|変数はレジスタまたはレジスタ相対メモリの場所に格納されません。|  
  
## <a name="remarks"></a>解説  
 列挙体の`VariableLocationType`メンバーは、メソッドによって返[されます](icordebugvariablehome-getlocationtype-method.md)。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)

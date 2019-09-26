---
title: CLRDataEnumMemoryFlags 列挙型
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67b85917be590bdba7ed3f10972ad39b731dbcdd
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274244"
---
# <a name="clrdataenummemoryflags-enumeration"></a>CLRDataEnumMemoryFlags 列挙型
[ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)メソッドへの呼び出しに含まれるメモリ領域を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|ミニダンプ (スパースメモリダンプ)。|  
|`CLRDATA_ENUM_MEM_HEAP`|完全なヒープダンプ。|  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](debugging-enumerations.md)

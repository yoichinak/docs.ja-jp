---
title: CorSymVarFlag 列挙体
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 21e92d8f2fb80c4c41d516ef281bf4fc8a75f4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176644"
---
# <a name="corsymvarflag-enumeration"></a>CorSymVarFlag 列挙体
変数がコンパイラで生成されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|指定された変数がコンパイラによって生成されることを示します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** コーシム.idl,コーシム.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断列挙体](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)

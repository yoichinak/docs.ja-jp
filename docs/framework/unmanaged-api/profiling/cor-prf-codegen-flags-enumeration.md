---
title: COR_PRF_CODEGEN_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 321318b63368ed6e57d235cf97d94485352f8686
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211362"
---
# <a name="corprfcodegenflags-enumeration"></a>COR_PRF_CODEGEN_FLAGS 列挙体
設定可能なコード生成フラグを定義、 [icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|関数はこの関数の本体にインライン化されません。 ただし、関数自体は、呼び出し元にインライン化でない可能性があります。|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|この関数の本体のすべての最適化を無効化されます。 ただし、関数自体できない可能性がありますが、呼び出し元にインライン化します。|  
  
## <a name="remarks"></a>Remarks  
 `COR_PRF_CODEGEN_FLAGS`列挙型を使用して、 [icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドを JIT 再コンパイルされた関数のコード生成を制御するプロファイラーを有効にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

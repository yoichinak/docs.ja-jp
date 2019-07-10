---
title: CREATE_ASM_NAME_OBJ_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 871ad81cd83c40d7299f39ede404e274b95b2ac0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778456"
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS 列挙型
属性を指定します、 [IAssemblyName インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクトは、によって作成時に、 [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|渡されたパラメーターが、テキスト id であることを示します。|  
|`CANOF_SET_DEFAULT_VALUES`|いくつかの既定値を設定します。|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|フレンド アセンブリのルール (名前と公開キーのみ) を確認します。 このメンバーは、内部使用のみです。|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|組み合わせ、`CANOF_PARSE_DISPLAY_NAME`と`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`フラグ。 このメンバーは、内部使用のみです。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyName インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [CreateAssemblyNameObject 関数](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [Fusion 列挙型](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

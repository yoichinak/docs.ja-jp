---
title: EBindPolicyLevels 列挙型
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e61acbb15844c5ddfc8b7aa98c41bb18c6e9ade5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769762"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels 列挙型
アセンブリのポリシーを変更または適用するレベルを指定するフラグを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|ポリシーが、管理者レベルで適用することを指定します。|  
|`ePolicyLevelApp`|ポリシーが、アプリケーション レベルで適用することを指定します。|  
|`ePolicyLevelHost`|ポリシーが、ホスト レベルで適用することを指定します。|  
|`ePolicyLevelNone`|ポリシー レベルのフラグを指定しません。|  
|`ePolicyLevelPublisher`|ポリシーが、パブリッシャーのレベルで適用することを指定します。|  
|`ePolicyLevelRetargetable`|ポリシーをさまざまなレベルで適用できる必要がありますを指定します。|  
|`ePolicyPortability`|ポリシーが、.NET Framework アセンブリの実装間で移植性をサポートする必要がありますを指定します。 参照してください、 [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)構成ファイルの要素。|  
|`ePolicyUnifiedToCLR`|共通言語ランタイム (CLR) のポリシーを統合する必要がありますを指定します。|  
  
## <a name="remarks"></a>Remarks  
 この列挙体は、のメソッドに渡される、 [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)アプリケーション ポリシーの変更を指定するインターフェイス。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

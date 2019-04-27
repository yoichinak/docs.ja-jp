---
title: EApiCategories 列挙型
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906374"
---
# <a name="eapicategories-enumeration"></a>EApiCategories 列挙型
ホストが部分的に信頼されたコードでの実行をブロックできる機能のカテゴリについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eAll`|クラスとその他で対応されるメンバーをすべて管理を指定します。`EApiCategories`フィールドは、部分的に信頼されたコードでの実行をブロックします。|  
|`eExternalProcessMgmt`|マネージ クラスとメンバーを作成、操作、および外部プロセスの破棄を部分的に信頼されたコードの実行をブロックすることを指定します。|  
|`eExternalThreading`|マネージ クラスとメンバーを作成、操作、および外部のスレッドの破棄を部分的に信頼されたコードの実行をブロックすることを指定します。|  
|`eMayLeakOnAbort`|マネージ型と中止にメモリをリークでした可能性のあるメンバーを部分的に信頼されたコードの実行をブロックすることを指定します。|  
|`eNoCategory`|部分的に信頼されたコードでの実行をブロックするマネージ コードのカテゴリがないを指定します。|  
|`eSecurityInfrastructure`|共通言語ランタイム (CLR) のセキュリティ インフラストラクチャを部分的に信頼されたコードによって使用されるをブロックするように指定します。|  
|`eSelfAffectingProcessMgmt`|マネージ クラスとメンバーの機能を持つホストされたプロセスに影響する可能性を部分的に信頼されたコードの実行をブロックすることを指定します。|  
|`eSelfAffectingThreading`|マネージ クラスとメンバーの機能を持つホストされるプロセスのスレッドに影響する可能性を部分的に信頼されたコードの実行をブロックすることを指定します。|  
|`eSharedState`|マネージ クラスおよび共有状態を公開するメンバーを部分的に信頼されたコードの実行をブロックすることを指定します。|  
|`eSynchronization`|共通言語ランタイム クラスとユーザー コードがロックを保持するメンバーを部分的に信頼されたコードの実行をブロックすることを指定します。|  
|`eUI`|マネージ クラスとメンバーを許可または人による操作を必要とするが部分的に信頼されたコードの実行をブロックすることを指定します。|  
  
## <a name="remarks"></a>Remarks  
 [Iclrhostprotectionmanager::setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)メソッドは、型のパラメーターを受け取る`EApiCategories`します。  
  
 `EApiCategories`列挙と`SetProtectedCategories`メソッドは直接関係をマネージ<xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>クラス。 マネージ クラスを併用、<xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>列挙型、値が対応に直接、`EApiCategories`を記載したカテゴリに対応する機能を公開するマネージ型とメンバーをマークする、値`EApiCategories`。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRHostProtectionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

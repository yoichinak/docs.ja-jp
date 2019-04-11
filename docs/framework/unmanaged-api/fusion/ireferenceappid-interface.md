---
title: IReferenceAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157197"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId インターフェイス
現在のスコープ内でアプリケーションの一意の識別子への参照を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|これによって参照されているアプリケーションのコードの識別子の文字列表現にポインターを取得します。`IReferenceAppId`します。|  
|`IReferenceAppId::put_CodeBase`|これによって参照されているアプリケーションのコードの識別子を設定`IReferenceAppId`します。|  
|`IReferenceAppId::EnumAppPath`|インターフェイス ポインターを取得、`IEnumReferenceIdentity`インスタンスを含む、 `IReferenceIdentity` this のメンバーを表すインスタンス`IReferenceAppId`します。|  
|`IReferenceAppId::get_SubscriptionId`|このサブスクリプションのトークンの識別子の文字列表現にポインターを取得します。`IReferenceAppId`します。|  
|`IReferenceAppId::put_SubscriptionId`|このサブスクリプションのトークンの識別子を設定`IReferenceAppId`を指定した文字列値。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IEnumReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [IReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)

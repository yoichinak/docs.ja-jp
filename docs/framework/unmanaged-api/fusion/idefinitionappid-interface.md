---
title: IDefinitionAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd705ef549de3a8018efe731ef8735ef7b6b915
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697239"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId インターフェイス
現在のスコープ内でアプリケーションを定義するコードの一意の識別子を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|このコードを表す書式設定された文字列を取得します。`IDefinitionAppId`オブジェクト。|  
|`IDefinitionAppId::put_Codebase`|このコードを設定`IDefinitionAppId`を指定したオブジェクトの書式設定された文字列値。|  
|`IDefinitionAppId::EnumAppPath`|インターフェイス ポインターを取得、 [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)現在のアプリケーション パス内のアセンブリを格納しているオブジェクト。|  
|`IDefinitionAppId::SetAppPath`|指定したによって参照される値を現在のスコープ内のアセンブリのアプリケーション パスを設定[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)オブジェクト。|  
|`IDefinitionAppId::get_SubscriptionId`|このサブスクリプションのトークンの識別子の文字列表現にポインターを取得します。`IDefinitionAppId`オブジェクト。|  
|`IDefinitionAppId::put_SubscriptionId`|このサブスクリプションのトークンの識別子を設定`IDefinitionAppId`オブジェクト指定した文字列値から。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)

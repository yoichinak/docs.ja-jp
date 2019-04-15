---
title: IDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ff23330f307c10eac134048de39a6e19a67c75b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192668"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity インターフェイス
現在のスコープ内でアプリケーションを定義するコードの一意のシグネチャを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|新しいインターフェイス ポインターを取得`IDefinitionIdentity`これと同じであるオブジェクト`IDefinitionIdentity`、指定した属性の変更を除く。|  
|`IDefinitionIdentity::EnumAttributes`|インターフェイス ポインターを取得、 [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)オブジェクトに関連付けられた属性を含む`IDefinitionIdentity`します。|  
|`IDefinitionIdentity::GetAttribute`|指定した名前空間には、指定した名前の属性の値を取得します。|  
|`IDefinitionIdentity::SetAttribute`|指定した値を指定した名前空間で指定した名前を持つ属性を設定します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)

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
ms.openlocfilehash: 84c595bfdcca84ee43a53e2ea913cc978ae0953e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796530"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity インターフェイス
現在のスコープ内のアプリケーションを定義するコードの一意の署名を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|指定した属性の変更を`IDefinitionIdentity`除き、この`IDefinitionIdentity`と同一の新しいオブジェクトへのインターフェイスポインターを取得します。|  
|`IDefinitionIdentity::EnumAttributes`|この`IDefinitionIdentity`に関連付けられている属性を格納している[IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)オブジェクトへのインターフェイスポインターを取得します。|  
|`IDefinitionIdentity::GetAttribute`|指定した名前空間内の指定した名前の属性の値を取得します。|  
|`IDefinitionIdentity::SetAttribute`|指定した名前空間の指定した名前を持つ属性を、指定した値に設定します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)

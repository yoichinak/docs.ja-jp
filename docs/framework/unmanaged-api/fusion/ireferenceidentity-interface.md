---
title: IReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796358"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity インターフェイス
コードオブジェクトの一意の署名への参照を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|指定した属性の変更を`IReferenceIdentity`除き、この`IReferenceIdentity`と同一の新しいインスタンスへのインターフェイスポインターを取得します。|  
|`IReferenceIdentity::EnumAttributes`|`IEnumIDENTITY_ATTRIBUTE` この`IReferenceIdentity`に関連付けられている属性を格納しているインスタンスへのインターフェイスポインターを取得します。|  
|`IReferenceIdentity::GetAttribute`|指定した名前を使用して、指定した名前空間の属性の値を取得します。|  
|`IReferenceIdentity::SetAttribute`|指定した名前空間と指定した名前を持つ属性を、指定した値に設定します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE インターフェイス](ienumidentity-attribute-interface.md)

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
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796371"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId インターフェイス
現在のスコープ内のアプリケーションの一意の識別子への参照を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|この`IReferenceAppId`によって参照されるアプリケーションのコード識別子の文字列形式へのポインターを取得します。|  
|`IReferenceAppId::put_CodeBase`|この`IReferenceAppId`によって参照されるアプリケーションのコード識別子を設定します。|  
|`IReferenceAppId::EnumAppPath`|この`IReferenceIdentity` `IEnumReferenceIdentity` のメンバーを表すインスタンスを格納しているインスタンスへのインターフェイスポインターを取得します。`IReferenceAppId`|  
|`IReferenceAppId::get_SubscriptionId`|この`IReferenceAppId`に対するサブスクリプションのトークン識別子の文字列形式へのポインターを取得します。|  
|`IReferenceAppId::put_SubscriptionId`|サブスクリプションのトークン識別子を指定された`IReferenceAppId`文字列値に設定します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IEnumReferenceIdentity インターフェイス](ienumreferenceidentity-interface.md)
- [IReferenceIdentity インターフェイス](ireferenceidentity-interface.md)

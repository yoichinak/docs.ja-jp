---
title: IEnumReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796430"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity インターフェイス
オブジェクトの`IReferenceIdentity`コレクションの列挙子として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|`IEnumReferenceIdentity` この`IEnumReferenceIdentity`と同じメンバーを含む新しいへのインターフェイスポインターを取得します。|  
|`IEnumReferenceIdentity::Next`|現在の`IReferenceIdentity`位置から開始して、指定した数のオブジェクトを取得します。|  
|`IEnumReferenceIdentity::Reset`|命令ポインターをこの`IEnumReferenceIdentity`の先頭に移動します。|  
|`IEnumReferenceIdentity::Skip`|現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IReferenceIdentity インターフェイス](ireferenceidentity-interface.md)

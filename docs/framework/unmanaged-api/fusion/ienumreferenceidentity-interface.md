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
ms.openlocfilehash: 766b17bae0c58d9872ff9c118f330ebc3220257e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123488"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity インターフェイス
コレクションの列挙子として機能`IReferenceIdentity`オブジェクト。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|新しいインターフェイス ポインターを取得`IEnumReferenceIdentity`これと同じメンバーを格納している`IEnumReferenceIdentity`します。|  
|`IEnumReferenceIdentity::Next`|指定した数を取得`IReferenceIdentity`オブジェクト、現在の位置で開始します。|  
|`IEnumReferenceIdentity::Reset`|これの先頭に、命令ポインターを移動`IEnumReferenceIdentity`します。|  
|`IEnumReferenceIdentity::Skip`|指定数の要素を現在の位置からでは、転送、命令ポインターを移動します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)

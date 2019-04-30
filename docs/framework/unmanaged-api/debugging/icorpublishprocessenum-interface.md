---
title: ICorPublishProcessEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5186df61eb82b29fcfa9776408498b748068e122
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993482"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum インターフェイス
サブクラスの[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)のコレクションを走査するメソッドを提供するインターフェイス[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)オブジェクト。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|指定した数を取得`ICorPublishProcess`コレクションの現在の位置からのインスタンス。|  
  
## <a name="remarks"></a>Remarks  
 `ICorPublishProcessEnum`インターフェイス、抽象インターフェイスのメソッドを実装[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)します。  
  
 `ICorPublishProcessEnum`によってインスタンスが作成された、 [icorpublish::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)メソッド。 コレクションのトラバーサル`ICorPublishProcess`オブジェクトは、時に指定されたフィルター条件に基づいて、`ICorPublishProcessEnum`インスタンスを作成します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)

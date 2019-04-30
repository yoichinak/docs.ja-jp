---
title: ICorPublishAppDomainEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f6d4af7c01f91dff77d6ba715ef845f523c7fb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993552"
---
# <a name="icorpublishappdomainenum-interface"></a>ICorPublishAppDomainEnum インターフェイス
サブクラスの[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)のコレクションを走査するメソッドを提供するインターフェイス[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)プロセス内に現在存在するオブジェクト。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|指定した数を取得`ICorPublishAppDomain`コレクションの現在の位置からのインスタンス。|  
  
## <a name="remarks"></a>Remarks  
 `ICorPublishAppDomainEnum`インターフェイス、抽象インターフェイスのメソッドを実装[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)

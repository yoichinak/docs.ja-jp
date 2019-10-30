---
title: ICorPublishEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: 7d083655326333f18ee98f8e84fff2ed182dde6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103463"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum インターフェイス
プロセスおよびアプリケーションドメインに関する情報の公開に使用される列挙子の抽象基本インターフェイスとして機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|この `ICorPublishEnum` オブジェクトのコピーを作成します。|  
|[GetCount メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|列挙に含まれる項目の数を取得します。|  
|[Reset メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|のカーソルを列挙体の先頭に移動します。|  
|[Skip メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|指定した数の項目だけ、列挙内でカーソルを前方に移動します。|  
  
## <a name="remarks"></a>Remarks  
 次の列挙子は `ICorPublishEnum`から派生します。  
  
- [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

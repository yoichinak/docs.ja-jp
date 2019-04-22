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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1eac0b9fe252e476f8ff781f2181a203886d3beb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160136"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum インターフェイス
プロセスとアプリケーション ドメインに関する情報の発行で使用される列挙子の抽象基底インターフェイスとして機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|このコピーを作成します`ICorPublishEnum`オブジェクト。|  
|[GetCount メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|列挙に含まれる項目の数を取得します。|  
|[Reset メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|列挙体の先頭のカーソルを移動します。|  
|[Skip メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|指定数の項目では、列挙体にカーソルを移動します。|  
  
## <a name="remarks"></a>Remarks  
 次の列挙子から派生して`ICorPublishEnum`:  
  
-   [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

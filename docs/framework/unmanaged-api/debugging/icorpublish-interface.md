---
title: ICorPublish インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121768"
---
# <a name="icorpublish-interface"></a>ICorPublish インターフェイス
プロセスに関する情報、およびそれらのプロセス内のアプリケーションドメインに関する情報を公開するための一般的なインターフェイスとして機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumProcesses メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|このコンピューター上で実行されているマネージプロセスを含む[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)インスタンスを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|指定した識別子を持つプロセスを表す[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)インスタンスを取得します。|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)

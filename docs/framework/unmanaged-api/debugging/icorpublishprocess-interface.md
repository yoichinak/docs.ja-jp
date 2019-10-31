---
title: ICorPublishProcess インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 04f6a088c5bbe96e3909ba600aa8ffab937abe2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140404"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess インターフェイス
プロセスについて表示される情報にアクセスするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumAppDomains メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|この `ICorPublishProcess`によって参照されるプロセス内のアプリケーションドメインを含む[ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)インスタンスを取得します。|  
|[GetDisplayName メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|この `ICorPublishProcess`によって参照されるプロセスの実行可能ファイルの完全パスを取得します。|  
|[GetProcessID メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|この `ICorPublishProcess`によって参照されるプロセスのオペレーティングシステム識別子を取得します。|  
|[IsManaged メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|この `ICorPublishProcess` によって参照されるプロセスがマネージコードを実行していることがわかっているかどうかを示す値を取得します。|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182963"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess インターフェイス
表示するプロセスについての情報にアクセスするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumAppDomains メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|取得、 [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)これによって参照されるプロセス内のアプリケーション ドメインを含むインスタンス`ICorPublishProcess`します。|  
|[GetDisplayName メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|これによって参照されるプロセスの実行可能ファイルの完全なパスを取得`ICorPublishProcess`します。|  
|[GetProcessID メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|これによって参照されるプロセスのオペレーティング システムの識別子を取得`ICorPublishProcess`します。|  
|[IsManaged メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|これによって、プロセスが参照されるかどうかを示す値を取得します`ICorPublishProcess`マネージ コードを実行することがわかっています。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)

---
title: ICorPublish::EnumProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb4096b0ae083e0b6c0598ea18cc8b33c2fdfe3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116296"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses メソッド
このコンピューターで実行されている管理対象プロセスの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `Type`  
 値、 [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)列挙型を取得するプロセスの種類を指定します。 現在のバージョンでのみ COR_PUB_MANAGEDONLY は有効です。  
  
 `ppIEnum`  
 アドレスへのポインター、 [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)プロセスの列挙子であるインスタンス。  
  
## <a name="remarks"></a>Remarks  
 プロセスの列挙子のコレクションがときに実行しているプロセスのスナップショットに基づいた、`EnumProcesses`メソッドが呼び出されます。 列挙子が終了する前に、または後に起動するプロセスは含まれません`EnumProcesses`が呼び出されます。  
  
 `EnumProcesses`このメソッドを複数回呼び出すことが[ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)プロセスの新しい最新の状態のコレクションを作成するインスタンス。 後続の呼び出しの既存のコレクションを受けませんが、`EnumProcesses`メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublish インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

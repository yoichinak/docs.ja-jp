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
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121799"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses メソッド
このコンピューター上で実行されているマネージプロセスの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `Type`  
 取得するプロセスの種類を指定する[COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)列挙体の値。 現在のバージョンでは、COR_PUB_MANAGEDONLY のみが有効です。  
  
 `ppIEnum`  
 プロセスの列挙子である[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)インスタンスのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 列挙子のプロセスのコレクションは、`EnumProcesses` メソッドが呼び出されたときに実行されているプロセスのスナップショットに基づいています。 列挙子には、`EnumProcesses` が呼び出された後に終了または開始されるプロセスは含まれません。  
  
 この[ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)インスタンスでは、`EnumProcesses` メソッドを複数回呼び出して、新しい最新のプロセスコレクションを作成することができます。 既存のコレクションは、`EnumProcesses` メソッドの後続の呼び出しの影響を受けません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublish インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

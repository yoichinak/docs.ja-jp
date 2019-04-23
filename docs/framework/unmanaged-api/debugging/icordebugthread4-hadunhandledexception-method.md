---
title: ICorDebugThread4::HadUnhandledException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12433786f353212c1ffbd57e9bf526c3ecc60e9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163632"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException メソッド
スレッドが未処理の例外をしたかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppBlockingObjectEnum`  
 [out]順序付けされた列挙体のアドレスへのポインター [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|スレッドは、未処理の例外の作成後にしました。|  
|S_FALSE|スレッドのハンドルされない例外がなかった。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、スレッドが未処理の例外をしたかどうかを示します。 ハンドルされない例外コールバックがトリガーされた時点でまたはネイティブの JIT アタッチが開始されると、このメソッドは S_OK を返す保証されます。 保証はありませんが、 [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)メソッドは、未処理の例外を返しますただし、場合、プロセスが続行されていない未処理の例外コールバックを取得した後、または時には。ネイティブ JIT アタッチします。 さらに、ことができます (ただし、可能性は低い) にネイティブ JIT アタッチがトリガーされた時点でハンドルされない例外では、複数のスレッドがあります。 このような場合は、JIT アタッチする例外がトリガーされるかを判断する方法はありません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugThread4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)

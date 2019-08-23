---
title: ICorDebugValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bb2f6333f306c8a19c8b2f67986b23819b74ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966862"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue インターフェイス
デバッグ中のプロセスの値を表します。 値には、読み取りまたは書き込みの値を指定できます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|このメソッドは現在実装されていません。|  
|[GetAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|このオブジェクトのアドレスを`ICorDebugValue`取得します。このアドレスは、デバッグ中のプロセスです。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|この`ICorDebugValue`オブジェクトのサイズ (バイト単位) を取得します。|  
|[GetType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|この`ICorDebugValue`オブジェクトのプリミティブ型を取得します。|  
  
## <a name="remarks"></a>Remarks  
 一般に、値オブジェクトの所有権は、返されるときに渡されます。 オブジェクトの終了時に、オブジェクトからの参照を削除するのは、受信者の責任です。  
  
 値が取得された場所によっては、プロセスが再開された後も値が有効なままにならないことがあります。 そのため、一般に、次のように、値は、は、「いいね[:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッドの呼び出し」で保持するべきではありません。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugValue3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

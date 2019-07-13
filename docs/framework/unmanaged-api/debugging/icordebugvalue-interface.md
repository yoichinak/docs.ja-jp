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
ms.openlocfilehash: bdc889dd6b2854654bfe43b24afbe4cc19863c80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993695"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue インターフェイス
デバッグ中のプロセスで値を表します。 値には、読み取り/書き込み値を指定できます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|このメソッドは現在実装されていません。|  
|[GetAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|このアドレスを取得`ICorDebugValue`デバッグ中の処理中であるオブジェクト。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|これのバイト単位のサイズを取得します。`ICorDebugValue`オブジェクト。|  
|[GetType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|このプリミティブ型を取得`ICorDebugValue`オブジェクト。|  
  
## <a name="remarks"></a>Remarks  
 一般に、返された場合、値オブジェクトの所有権が渡されます。 受信デバイスが、オブジェクトが完了したら、オブジェクトからの参照を削除する責任を負います。  
  
 ここから値を取得した、によって値削除される有効なプロセスが再開されます。 そのため、一般にの値はありませんが保持呼び出しの間で、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッド。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugValue3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

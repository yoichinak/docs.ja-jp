---
title: ICorDebugProcess5::GetGCHeapInformation メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50b682a7b3a4aadf7559120745265ef266cf2870
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948747"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>ICorDebugProcess5::GetGCHeapInformation メソッド
現在の列挙可能かどうかなど、ガベージ コレクション ヒープに関する一般的な情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pHeapInfo`  
 [out]ポインターを[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)ガベージ コレクション ヒープに関する一般的な情報を提供する値。  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugProcess5::GetGCHeapInformation`ヒープを列挙する前にメソッドを呼び出す必要がありますまたは構造体のガベージ コレクションには、プロセスのことを確認するための個々 のヒープ領域は、現在有効です。 コレクションが進行中は、ガベージ コレクション ヒープを処理することはできません。 それ以外の場合、列挙体は、無効なガベージ コレクションの構造をキャプチャする場合があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugMutableDataTarget::WriteVirtual メソッド
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fba970de6e5882d3cbe9be17b5b49be5a3e81aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171653"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual メソッド
ターゲット プロセスのアドレス空間にメモリを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in] `pBuffer` の内容の書き込み先のアドレスです。  
  
 `pBuffer`  
 [in] 書き込むバイト数が格納されているバイト配列へのポインター。  
  
 `address`  
 [in] `pBuffer` のバイト数。  
  
## <a name="return-value"></a>戻り値  
 正常に完了した場合は `S_OK`、失敗した場合はその他の `HRESULT`。  
  
## <a name="remarks"></a>Remarks  
 バイトを書き込むことができない場合、メソッド呼び出しは失敗し、ターゲット アドレス空間のバイトは変更されません。 (それ以外の場合、ターゲットは不整合な状態になり、デバッグの信頼性がさらに低下します。)  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMutableDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

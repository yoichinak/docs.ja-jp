---
title: ICorDebugModule3::CreateReaderForInMemorySymbols メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfe83707b6354c42a4c3c81e911918b2ea79ec4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108915"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols メソッド
動的モジュールのデバッグのシンボル リーダーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>パラメーター  
 riid  
 [in]返す COM インターフェイスの IID。 通常、これは、 [ISymUnmanagedReader インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)します。  
  
 ppObj  
 [out]返されるインターフェイスへのポインターへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 リーダーが正常に作成します。  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 モジュールは、メモリ内または動的モジュールではありません。  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 シンボルは、アプリケーションで指定されていないまたはまだ提供されていません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 リーダーを作成できません。  
  
## <a name="remarks"></a>Remarks  
 このメソッドも、メモリ内の (非動的) モジュールのシンボル リーダー オブジェクトを作成するために使用のみするシンボルが利用可能に最初 (で示される、 [UpdateModuleSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)コールバック)。  
  
 このメソッドが呼び出されるたびに、新しいリーダーのインスタンスを返します (など[CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance))。 そのため、デバッガーが結果をキャッシュして、基になるデータが変更されたときにのみ、新しいインスタンスを要求する必要があります (つまりとき、 [LoadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)コールバックを受信した)。  
  
 最初の型が読み込まれるまで動的モジュールは使用可能なすべてのシンボルはありません (で示されている、 [LoadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)コールバック)。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

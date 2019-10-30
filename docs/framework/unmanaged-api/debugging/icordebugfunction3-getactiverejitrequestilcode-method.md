---
title: ICorDebugFunction3::GetActiveReJitRequestILCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 0e706861237ed08700ef0abcc424b6f1de5f462c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134638"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 アクティブな ReJIT 要求から IL を含む、[コード](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)へのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppReJitedILCode`  
 アクティブな ReJIT 要求からの、IL へのポインター。  
  
## <a name="remarks"></a>Remarks  
 この `ICorDebugFunction3` オブジェクトによって表示されるメソッドがアクティブな ReJIT 要求を持っている場合、`ppReJitedILCode` は IL へのポインターを返します。 一般的なケースであるアクティブな要求がない場合、`ppReJitedILCode` は**null**になります。  
  
 ReJIT 要求は、 [ICorProfilerCallback4:: GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)メソッドの呼び出しから実行が戻った直後にアクティブになります。 これは、まだ JIT コンパイルされていない可能性があり、スレッドはコードの元のバージョンで実行中の可能性があります。 ReJIT 要求は、 [ICorProfilerInfo4:: RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)メソッドへのプロファイラーの呼び出し中に非アクティブになります。 LI が戻された後であっても、スレッドは JIT 再コンパイル (ReJIT) されたコードで実行中の可能性があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugFunction3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: ハウツーガイド](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)

---
title: 'ICorProfilerInfo7:: ReadInMemorySymbols'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955371"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7:: ReadInMemorySymbols
[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 メモリ内シンボルストリームからバイトを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleId`  
 からメモリ内ストリームを格納しているモジュールの識別子。  
  
 `symbolsReadOffset`  
 からメモリ内ストリーム内でバイトの読み取りを開始する位置のオフセット。  
  
 `pSymbolBytes`  
 入出力データがコピーされるバッファーへのポインター。 バッファーには、 `countSymbolBytes`使用可能な領域が必要です。  
  
 `countSymbolBytes`  
 からコピーするバイト数。  
  
 `pCountSymbolBytesRead`  
 入出力メソッドから制御が戻るときに、実際に読み取られたバイト数を格納します。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`0以外のバイト数が読み取られた場合は。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`モジュールがを使用して<xref:System.Reflection.Emit>作成された場合は。  
  
## <a name="remarks"></a>Remarks  
 メソッド`ReadInMemorySymbols`は、インメモリ`countSymbolBytes`ストリーム内のオフセット`symbolsReadOffset`を開始位置として、データの読み取りを試みます。 データはに`pSymbolBytes`コピーされます。これには`countSymbolBytes` 、使用可能な領域があることが予想されます。     `pCountSymbolsBytesRead`実際に読み取られたバイト数を格納します。ストリーム`countSymbolBytes`の末尾に到達した場合よりも小さくなることがあります。  
  
> [!NOTE]
> 現在の実装では、リフレクションはサポートされていません。 モジュールがリフレクションを使用して作成された場合、メソッド`CORPROF_E_MODULE_IS_DYNAMIC`はを返します。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)

---
title: 'ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 157b0e215f8afa58cccb3d54a65baa9c307ba966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955428"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド
[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 メモリ内シンボルストリームの長さを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleId`  
 からメモリ内ストリームを格納しているモジュールの識別子。  
  
 Pcountシンボルバイト数  
 入出力メソッドから制御が`DWORD`戻るときに、ストリーム長がバイト単位で格納されている値へのポインター。  
  
## <a name="return-value"></a>戻り値  
 メモリストリームの`S_OK`長さがゼロ (0) であっても、このメソッドはを返します。  
  
 メソッドがを`CORPROF_E_MODULE_IS_DYNAMIC`使用して<xref:System.Reflection.Emit?displayProperty=nameWithType>作成された場合、メソッドはを返します。  
  
## <a name="remarks"></a>Remarks  
 モジュールにメモリ内シンボルがある場合は、ストリームの長さがに`pCountSymbolBytes`配置されます。 モジュールにメモリ内シンボル`*pCountSymbolBytes = 0`がない場合は。  
  
> [!NOTE]
> 現在の実装では、リフレクションはサポートされていません。 モジュールがリフレクションを使用して作成された場合、メソッド`CORPROF_E_MODULE_IS_DYNAMIC`はを返します。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)

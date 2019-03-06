---
title: ICorProfilerInfo7::ReadInMemorySymbols
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
ms.openlocfilehash: 4f42345977f69dd27294a44b4c007ab08d2ec6f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468352"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 以降のバージョンでサポート]  
  
 メモリ内のシンボルのストリームからバイトを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]メモリ内のストリームを含むモジュールの識別子です。  
  
 `symbolsReadOffset`  
 [in]バイトの読み取りを開始する位置のメモリ内ストリーム内のオフセット。  
  
 `pSymbolBytes`  
 [out]データのコピー先バッファーへのポインター。 バッファーがあります`countSymbolBytes`使用可能な領域。  
  
 `countSymbolBytes`  
 [in]コピーするバイト数。  
  
 `pCountSymbolBytesRead`  
 [out]メソッドが戻るとき、実際に読み取られたバイト数を格納します。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`、読み取られたバイト数を 0 以外の場合。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`を使用して、モジュールが作成された場合<xref:System.Reflection.Emit>します。  
  
## <a name="remarks"></a>Remarks  
 `ReadInMemorySymbols`メソッドの読み取りを試みます`countSymbolBytes`オフセットから始まるデータの`symbolsReadOffset`メモリ内ストリーム内で。 データをコピー`pSymbolBytes`が想定されています`countSymbolBytes`使用可能な領域。     `pCountSymbolsBytesRead` 実際の少ない可能性がありますが、読み取られたバイト数を含むより`countSymbolBytes`ストリームの末尾に達した場合。  
  
> [!NOTE]
>  現在の実装は、Reflection.Emit をサポートしていません。 かどうか、モジュールは、Reflection.Emit を使用して作成された、メソッドを返します`CORPROF_E_MODULE_IS_DYNAMIC`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)

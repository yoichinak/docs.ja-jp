---
title: ICorProfilerInfo7::GetInMemorySymbolsLength メソッド
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
ms.openlocfilehash: 422fdfef6bea40e0f4bcc7447df8dba1eab2896e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146095"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7::GetInMemorySymbolsLength メソッド
[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 メモリ内のシンボルのストリームの長さを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]メモリ内のストリームを含むモジュールの識別子です。  
  
 pCountSymbolBytes  
 [out]ポインターを`DWORD`メソッドが戻るときに、バイト単位のストリームの長さを格納する値。  
  
## <a name="return-value"></a>戻り値  
 メソッドを返します`S_OK`かどうかメモリ ストリームの長さを決定できますはゼロ (0) 場合でもです。  
  
 メソッドを返します`CORPROF_E_MODULE_IS_DYNAMIC`を使用して、メソッドが作成された場合<xref:System.Reflection.Emit?displayProperty=nameWithType>します。  
  
## <a name="remarks"></a>Remarks  
 モジュールは、メモリ内のシンボルには、ストリームの長さに置かれます。`pCountSymbolBytes`します。 モジュールは、メモリ内のシンボルを持っていない場合`*pCountSymbolBytes = 0`します。  
  
> [!NOTE]
>  現在の実装は、Reflection.Emit をサポートしていません。 かどうか、モジュールは、Reflection.Emit を使用して作成された、メソッドを返します`CORPROF_E_MODULE_IS_DYNAMIC`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)

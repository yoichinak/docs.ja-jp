---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f3c0a3525c87fbf39199c15a6619ff4a0d2acc42
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973852"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3 メソッド
  
  マネージコード命令ポインターを FunctionID にマップします。 このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。    
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```  
  
#### <a name="parameters"></a>パラメーター  
 `ip`  
 からマネージコード内の命令ポインター。  

 `pFunctionId`  
 入出力関数 ID。  
  
 `pReJitId`  
 入出力関数の JIT 再コンパイルバージョンの id。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。 これは[GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)のスーパーセットであり、メタデータを持つ関数に対してのみ機能します。
  

## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [![Net_current_v472plus](../../../../includes/net-current-v472plus.md)を含める  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo8 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)


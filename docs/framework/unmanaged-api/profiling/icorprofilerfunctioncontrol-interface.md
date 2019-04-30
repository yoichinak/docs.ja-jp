---
title: ICorProfilerFunctionControl インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 721ee27522b316a561e2f64a322c225cb85a44c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992174"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl インターフェイス
特定のメソッドを再コンパイルする時に JIT コンパイラーがコードをどのように生成するかを制御するために、コード プロファイラーが共通言語ランタイム (CLR) と通信できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[SetCodegenFlags メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|1 つまたは複数のフラグを設定、 [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)を - just-in-time (JIT) のコード生成を制御する列挙型の再コンパイルされた関数。|  
|[SetILFunctionBody メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|メソッドの中間共通言語 (CIL) 本体を置換します。|  
|[SetILInstrumentedCodeMap メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorProfilerFunctionControl` インターフェイスは、単一の再コンパイルされた関数に対してコード生成を制御するためにメソッドを提供します。 プロファイラーは、使用して、このインターフェイスのインスタンスを取得、 [icorprofilercallback 4::getrejitparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)コールバック。 `ICorProfilerFunctionControl` の各インスタンスは一つの関数の全てのインスタンスを制御します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)

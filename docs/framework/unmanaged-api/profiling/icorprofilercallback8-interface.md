---
title: ICorProfilerCallback8 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125568"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 インターフェイス
[.NET Framework 4.7 以降のバージョンでサポートされます]  

 サブクラス[ICorProfilerCallback7](icorprofilercallback7-interface.md)動的メソッドの JIT コンパイルが開始して完了したことをプロファイラーに通知する、共通言語ランタイムで使用されるコールバック メソッドを提供します。 
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted メソッド](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|動的メソッドの JIT コンパイルが開始されたことをプロファイラーに通知します。|  
|[DynamicMethodJITCompilationFinished メソッド](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|動的メソッドの JIT コンパイルが完了したことをプロファイラーに通知します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback9 インターフェイス](icorprofilercallback9-interface.md)
